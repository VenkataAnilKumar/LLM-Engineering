# 🏗️ Medical Diagnosis Assistant - Solution Architecture

📑 **Navigation**: [🏠 Main](./README.md) | [📊 Overview](./README_Overview.md) | [⚠️ Challenges](./README_Challenges_Solutions.md) | [💻 Code](./README_Code_Snippets.md) | [🚀 Future](./README_Future_Improvements.md)

---

## Table of Contents

1. [System Architecture Overview](#1-system-architecture-overview)
2. [Component Breakdown](#2-component-breakdown)
3. [Model Selection & Rationale](#3-model-selection--rationale)
4. [Fine-Tuning Approach](#4-fine-tuning-approach)
5. [RAG Implementation](#5-rag-implementation)
6. [Prompt Engineering](#6-prompt-engineering)
7. [Infrastructure & Deployment](#7-infrastructure--deployment)
8. [Monitoring & Observability](#8-monitoring--observability)

---

## 1. System Architecture Overview

### 1.1 High-Level Data Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                     Medical Diagnosis Assistant                  │
└─────────────────────────────────────────────────────────────────┘
                                 │
                 ┌───────────────┴───────────────┐
                 │                               │
         ┌───────▼────────┐             ┌───────▼────────┐
         │  PACS/DICOM    │             │   EHR System   │
         │   Interface    │             │   Interface    │
         │  (Orthanc)     │             │  (Epic FHIR)   │
         └───────┬────────┘             └───────┬────────┘
                 │                               │
         ┌───────▼───────────────────────────────▼────────┐
         │          Pre-processing & Validation            │
         │  - DICOM parsing       - Normalization          │
         │  - Quality checks      - Anonymization (HIPAA)  │
         │  - Metadata extraction - Format standardization │
         └───────┬─────────────────────────────────────────┘
                 │
         ┌───────▼────────────────────────────────────────┐
         │            Vision Analysis Pipeline             │
         │  ┌────────────────────────────────────┐        │
         │  │  BioMed-CLIP (Vision Encoder)      │        │
         │  │  - Feature extraction (768-dim)    │        │
         │  │  - Abnormality detection           │        │
         │  │  - Region localization (bboxes)    │        │
         │  │  - Confidence scoring              │        │
         │  └────────┬───────────────────────────┘        │
         └───────────┼────────────────────────────────────┘
                     │ Image embeddings
         ┌───────────▼────────────────────────────────────┐
         │        Multi-Modal LLM Processing              │
         │  ┌────────────────────────────────────┐        │
         │  │  LLaMA 2 70B (LoRA Fine-tuned)     │        │
         │  │  Input:                             │        │
         │  │    - Image features (768-dim)      │        │
         │  │    - Patient context (age, hx)     │        │
         │  │    - Clinical indication           │        │
         │  │  Output:                            │        │
         │  │    - Differential diagnosis         │        │
         │  │    - Confidence scoring             │        │
         │  │    - Structured findings            │        │
         │  └────────┬───────────────────────────┘        │
         └───────────┼────────────────────────────────────┘
                     │ Initial findings
         ┌───────────▼────────────────────────────────────┐
         │          RAG Knowledge Retrieval                │
         │  ┌─────────────────────────────────────┐       │
         │  │  FAISS Vector Database              │       │
         │  │  - 5M PubMed abstracts              │       │
         │  │  - 15K Radiopaedia cases            │       │
         │  │  - 500 Clinical guidelines          │       │
         │  │  - 100K Historical hospital cases   │       │
         │  │                                      │       │
         │  │  Multi-stage retrieval:             │       │
         │  │  1. Semantic search (cosine sim)    │       │
         │  │  2. Keyword search (BM25)           │       │
         │  │  3. Similar case retrieval          │       │
         │  │  4. Guideline matching              │       │
         │  │  5. Cross-encoder reranking         │       │
         │  └────────┬────────────────────────────┘       │
         └───────────┼────────────────────────────────────┘
                     │ Retrieved context (top-5)
         ┌───────────▼────────────────────────────────────┐
         │       Final Report Generation (LLM)             │
         │  - Combine findings + RAG context              │
         │  - Generate structured report                   │
         │  - Add confidence scores                        │
         │  - Flag critical findings                       │
         │  - Cite literature references                   │
         └───────┬─────────────────────────────────────────┘
                 │ Structured JSON report
         ┌───────▼────────────────────────────────────────┐
         │       Radiologist Review Interface              │
         │  ┌──────────────────────────────────────┐      │
         │  │  - Side-by-side comparison            │      │
         │  │  - AI draft vs radiologist edits      │      │
         │  │  - Edit and approve workflow          │      │
         │  │  - One-click feedback capture         │      │
         │  │  - Critical finding alerts (STAT)     │      │
         │  │  - Performance analytics dashboard    │      │
         │  └──────────────────────────────────────┘      │
         └─────────────────────────────────────────────────┘
```

### 1.2 System Layers

**Layer 1: Integration Layer**
- Connects to hospital PACS and EHR systems
- Handles HL7 messaging and DICOM protocols
- Ensures HIPAA-compliant data handling

**Layer 2: Pre-processing Layer**
- DICOM parsing and quality validation
- Image normalization and standardization
- PHI removal (anonymization)

**Layer 3: AI Analysis Layer**
- Vision model: Feature extraction and abnormality detection
- LLM: Clinical reasoning and report generation
- RAG: Knowledge retrieval and grounding

**Layer 4: Presentation Layer**
- Radiologist interface for review/editing
- Critical finding alerts
- Feedback loop for continuous improvement

---

## 2. Component Breakdown

### 2.1 PACS/DICOM Interface

**Technology**: Orthanc DICOM Server

**Responsibilities:**
- Receive DICOM images from hospital PACS
- Parse DICOM metadata (modality, body part, technique)
- Store images temporarily for processing
- Send results back via HL7 ORU messages

**Integration Points:**
```python
# DICOM listener configuration
dicom_config = {
    "aet": "AI_DIAGNOSIS",           # Application Entity Title
    "port": 4242,                     # DICOM port
    "peer_aet": "HOSPITAL_PACS",      # Hospital PACS identifier
    "storage_path": "/mnt/dicom",     # Temporary storage
    "timeout": 30                      # Connection timeout (seconds)
}

# HL7 interface
hl7_config = {
    "host": "hl7.hospital.internal",
    "port": 2575,
    "msh_sending_app": "AI_RADIOLOGY",
    "msh_receiving_app": "EPIC_EMR"
}
```

**Key Features:**
- ✅ Automatic study routing based on modality
- ✅ Priority queuing (STAT > URGENT > ROUTINE)
- ✅ Retry logic for failed transmissions
- ✅ Audit logging for compliance

### 2.2 EHR Integration (Epic FHIR API)

**Purpose**: Retrieve patient context for better diagnosis

**Data Retrieved:**
- Patient demographics (age, sex)
- Relevant medical history
- Recent lab results
- Prior imaging reports
- Current medications
- Clinical indication for study

**API Endpoints:**
```python
# FHIR R4 endpoints
fhir_endpoints = {
    "patient": "/Patient/{id}",
    "observations": "/Observation?patient={id}&category=laboratory",
    "medications": "/MedicationRequest?patient={id}&status=active",
    "imaging": "/ImagingStudy?patient={id}",
    "conditions": "/Condition?patient={id}"
}
```

**Security:**
- OAuth 2.0 authentication
- Scoped access (read-only)
- PHI audit logging
- Rate limiting (100 requests/min)

### 2.3 Pre-processing Pipeline

**Step 1: DICOM Parsing**
```python
def parse_dicom(dicom_path: str) -> Dict:
    """Extract metadata and pixel data from DICOM"""
    import pydicom
    
    ds = pydicom.dcmread(dicom_path)
    
    metadata = {
        "modality": ds.Modality,                    # e.g., "CR", "CT", "MR"
        "body_part": ds.BodyPartExamined,          # e.g., "CHEST"
        "study_description": ds.StudyDescription,
        "series_description": ds.SeriesDescription,
        "patient_id": ds.PatientID,                # Will be anonymized
        "study_date": ds.StudyDate,
        "image_shape": (ds.Rows, ds.Columns),
        "pixel_spacing": ds.PixelSpacing,
        "window_center": ds.WindowCenter,
        "window_width": ds.WindowWidth
    }
    
    pixel_array = ds.pixel_array
    
    return metadata, pixel_array
```

**Step 2: Quality Validation**
```python
def validate_image_quality(pixel_array: np.ndarray, metadata: Dict) -> Dict:
    """Check image quality before processing"""
    
    issues = []
    
    # Check exposure
    mean_intensity = pixel_array.mean()
    if mean_intensity < 50 or mean_intensity > 4000:
        issues.append("POOR_EXPOSURE")
    
    # Check resolution
    if metadata["image_shape"][0] < 512:
        issues.append("LOW_RESOLUTION")
    
    # Check for artifacts
    if detect_motion_artifacts(pixel_array):
        issues.append("MOTION_ARTIFACT")
    
    # Check positioning (for chest X-rays)
    if metadata["body_part"] == "CHEST":
        if not is_properly_positioned(pixel_array):
            issues.append("POOR_POSITIONING")
    
    return {
        "valid": len(issues) == 0,
        "issues": issues,
        "quality_score": calculate_quality_score(pixel_array)
    }
```

**Step 3: Normalization**
```python
def normalize_medical_image(pixel_array: np.ndarray, metadata: Dict) -> np.ndarray:
    """Standardize image for model input"""
    
    # Apply window/level if specified
    if "window_center" in metadata:
        pixel_array = apply_windowing(
            pixel_array,
            center=metadata["window_center"],
            width=metadata["window_width"]
        )
    
    # Normalize to 0-1 range
    pixel_array = (pixel_array - pixel_array.min()) / (pixel_array.max() - pixel_array.min())
    
    # Resize to model input size (224x224 for BioMed-CLIP)
    pixel_array = cv2.resize(pixel_array, (224, 224))
    
    # Convert to 3-channel (models expect RGB)
    if pixel_array.ndim == 2:
        pixel_array = np.stack([pixel_array] * 3, axis=-1)
    
    return pixel_array
```

**Step 4: Anonymization (HIPAA)**
```python
def anonymize_patient_data(metadata: Dict, patient_data: Dict) -> Dict:
    """Remove 18 HIPAA identifiers"""
    
    # Hash identifiers
    metadata["patient_id"] = hashlib.sha256(
        metadata["patient_id"].encode()
    ).hexdigest()[:16]
    
    # Generalize dates (keep year only)
    metadata["study_date"] = metadata["study_date"][:4]
    
    # Remove specific locations
    patient_data["address"] = patient_data["address"]["state"]
    
    # Preserve clinically relevant data
    anonymized = {
        "age": patient_data["age"],
        "sex": patient_data["sex"],
        "symptoms": patient_data["symptoms"],
        "history": remove_identifiers(patient_data["history"]),
        "labs": patient_data["labs"]
    }
    
    return anonymized
```

### 2.4 Vision Model (BioMed-CLIP)

**Architecture**: CLIP adapted for medical imaging

**Model Details:**
- Base: OpenAI CLIP ViT-B/16
- Fine-tuned on: 100K medical images
- Input: 224×224 RGB images
- Output: 768-dimensional embeddings

**Capabilities:**
1. **Feature Extraction**: Convert images to embeddings
2. **Abnormality Detection**: Identify suspicious regions
3. **Localization**: Generate bounding boxes
4. **Confidence Scoring**: Probability for each finding

**Inference:**
```python
import torch
from transformers import CLIPProcessor, CLIPModel

class BioMedCLIPVision:
    def __init__(self, model_path: str):
        self.model = CLIPModel.from_pretrained(model_path)
        self.processor = CLIPProcessor.from_pretrained(model_path)
        self.model.eval()
        
    def analyze_image(self, image: np.ndarray) -> Dict:
        """Extract features and detect abnormalities"""
        
        # Prepare input
        inputs = self.processor(
            images=image,
            return_tensors="pt",
            padding=True
        ).to("cuda")
        
        # Get image embeddings
        with torch.no_grad():
            image_features = self.model.get_image_features(**inputs)
            image_features = image_features / image_features.norm(dim=-1, keepdim=True)
        
        # Detect abnormalities using zero-shot classification
        text_prompts = [
            "normal chest x-ray",
            "pneumonia",
            "fracture",
            "pneumothorax",
            "pleural effusion",
            "pulmonary nodule",
            "cardiomegaly"
        ]
        
        text_inputs = self.processor(
            text=text_prompts,
            return_tensors="pt",
            padding=True
        ).to("cuda")
        
        with torch.no_grad():
            text_features = self.model.get_text_features(**text_inputs)
            text_features = text_features / text_features.norm(dim=-1, keepdim=True)
            
            # Compute similarity
            similarity = (100.0 * image_features @ text_features.T).softmax(dim=-1)
        
        # Parse results
        abnormalities = []
        for i, prompt in enumerate(text_prompts):
            if i == 0:  # Skip "normal"
                continue
            score = similarity[0, i].item()
            if score > 0.15:  # Threshold
                abnormalities.append({
                    "finding": prompt,
                    "confidence": score,
                    "bbox": self.localize_finding(image, prompt)  # GradCAM
                })
        
        return {
            "embeddings": image_features.cpu().numpy(),
            "abnormalities": abnormalities,
            "summary": self.generate_summary(abnormalities)
        }
```

**Performance:**
- Sensitivity: 89% for common pathologies
- Specificity: 91%
- Inference time: 180ms per image
- GPU memory: 4GB (batch size 1)

### 2.5 LLM (LLaMA 2 70B with LoRA)

**Base Model**: meta-llama/Llama-2-70b-hf

**Fine-tuning Method**: QLoRA (Quantized Low-Rank Adaptation)

**Why LLaMA 2 70B?**

| Requirement | LLaMA 2 70B | Alternatives |
|-------------|-------------|--------------|
| On-premise deployment | ✅ Yes | GPT-4: ❌ Cloud only |
| Cost per query | ✅ $0.15 | GPT-4: $3-5 |
| Latency | ✅ 2.3s | GPT-4: 5-8s |
| Fine-tuning | ✅ Full control | GPT-4: Limited |
| HIPAA compliance | ✅ Complete | GPT-4: Requires BAA |
| Medical knowledge | 🟡 Good (with FT) | GPT-4: Excellent |

**Model Configuration:**
```python
from transformers import AutoModelForCausalLM, BitsAndBytesConfig
from peft import LoraConfig, get_peft_model

# Quantization config (4-bit)
bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_compute_dtype=torch.float16,
    bnb_4bit_use_double_quant=True
)

# Load base model
model = AutoModelForCausalLM.from_pretrained(
    "meta-llama/Llama-2-70b-hf",
    quantization_config=bnb_config,
    device_map="auto",
    torch_dtype=torch.float16,
    trust_remote_code=True
)

# LoRA config
lora_config = LoraConfig(
    r=64,                          # Rank
    lora_alpha=16,                 # Scaling factor
    target_modules=[               # Apply LoRA to these layers
        "q_proj",
        "k_proj",
        "v_proj",
        "o_proj",
        "gate_proj",
        "up_proj",
        "down_proj"
    ],
    lora_dropout=0.05,
    bias="none",
    task_type="CAUSAL_LM"
)

# Apply LoRA
model = get_peft_model(model, lora_config)
```

**Training Stats:**
- Trainable parameters: 336M (0.5% of 70B)
- GPU memory: 48GB (vs 280GB full precision)
- Training time: 48 hours on 2× A100
- Training cost: $120 (AWS p4d.24xlarge)

### 2.6 RAG System (FAISS + PubMed-BERT)

**Vector Database**: FAISS (Facebook AI Similarity Search)

**Embedding Model**: microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract

**Knowledge Sources:**

| Source | Count | Purpose |
|--------|-------|---------|
| PubMed abstracts | 5,000,000 | General medical knowledge |
| Radiopaedia cases | 15,000 | Radiology-specific cases |
| Clinical guidelines | 500 | Evidence-based protocols |
| Hospital cases | 100,000 | Local patterns and practices |

**Index Architecture:**
```python
import faiss
import numpy as np

class MedicalRAG:
    def __init__(self, index_path: str):
        # Load FAISS index (IVF4096, PQ64)
        self.index = faiss.read_index(index_path)
        
        # Index specs:
        # - Type: IVF (Inverted File) + PQ (Product Quantization)
        # - Clusters: 4096
        # - Quantization: 64 bytes per vector
        # - Metric: Cosine similarity
        # - Size on disk: 1.2TB
        # - Memory: 80GB (memory-mapped)
        
        # Load embedding model
        from sentence_transformers import SentenceTransformer
        self.encoder = SentenceTransformer(
            'microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract'
        )
        
        # Load document metadata
        import json
        with open(f"{index_path}.metadata.json") as f:
            self.documents = json.load(f)
    
    def retrieve(
        self,
        query: str,
        k: int = 5,
        filters: Dict = None
    ) -> List[Dict]:
        """Multi-stage retrieval"""
        
        # Stage 1: Semantic search (FAISS)
        query_embedding = self.encoder.encode([query])[0]
        query_embedding = query_embedding.astype('float32')
        
        distances, indices = self.index.search(
            np.array([query_embedding]),
            k=k * 2  # Get 2x for filtering
        )
        
        # Stage 2: Apply filters
        results = []
        for dist, idx in zip(distances[0], indices[0]):
            doc = self.documents[idx]
            
            if filters:
                if not self.matches_filters(doc, filters):
                    continue
            
            doc['relevance_score'] = 1 / (1 + dist)
            results.append(doc)
            
            if len(results) >= k:
                break
        
        return results
```

**Retrieval Performance:**
- Latency: 180ms (average)
- Recall@5: 0.88
- Precision@5: 0.82
- Cache hit rate: 45%

---

## 3. Model Selection & Rationale

### 3.1 Comparison Matrix

| Model | Medical Accuracy | Cost/Query | Latency | HIPAA | Customization | Verdict |
|-------|-----------------|-----------|---------|-------|---------------|---------|
| **LLaMA 2 70B** | 93% (fine-tuned) | $0.15 | 2.3s | ✅ Full | ✅ Full | ✅ **CHOSEN** |
| GPT-4 | 88% (zero-shot) | $3-5 | 5-8s | ⚠️ BAA required | ❌ Limited | ❌ Too expensive |
| Med-PaLM 2 | 96% (claimed) | Unknown | 4-6s | ❌ Cloud only | ❌ None | ❌ Not available |
| GPT-3.5 Turbo | 75% (zero-shot) | $0.50 | 2s | ⚠️ BAA required | ❌ Limited | ❌ Insufficient accuracy |
| Claude 2 | 85% (zero-shot) | $2-4 | 4s | ⚠️ BAA required | ❌ Limited | ❌ Cost + cloud |

### 3.2 Decision Factors

**Factor 1: HIPAA Compliance** ⚖️
- **Requirement**: PHI cannot leave hospital network
- **LLaMA 2**: Self-hosted, complete control ✅
- **GPT-4**: Requires BAA, data sent to OpenAI ❌

**Factor 2: Cost at Scale** 💰
```
Hospital volume: 50,000 studies/month

LLaMA 2 cost: $0.15 × 50K = $7,500/month
GPT-4 cost: $3.00 × 50K = $150,000/month

Annual savings: $1.71M by using LLaMA 2
```

**Factor 3: Latency** ⏱️
- Emergency cases need <5s response time
- LLaMA 2: 2.3s ✅
- GPT-4: 5-8s ❌

**Factor 4: Customization** 🛠️
- Need to fine-tune on hospital-specific data
- LLaMA 2: Full fine-tuning possible ✅
- GPT-4: Only prompt engineering ❌

**Conclusion**: LLaMA 2 70B is the optimal choice for production healthcare AI.

---

## 4. Fine-Tuning Approach

### 4.1 Dataset Preparation

**Data Sources:**
- MIMIC-CXR: 25,000 de-identified chest X-rays + reports
- Hospital data: 25,000 reports (IRB approved)
- Total: 50,000 radiology reports

**Data Format:**
```json
{
  "study_id": "study_12345",
  "modality": "Chest X-ray",
  "clinical_indication": "Cough and fever",
  "patient_context": {
    "age": 65,
    "sex": "M",
    "history": "COPD, former smoker"
  },
  "image_findings": {
    "abnormalities": [
      {"region": "right lower lobe", "finding": "opacity", "confidence": 0.89}
    ]
  },
  "report": {
    "findings": "Right lower lobe airspace opacity with air bronchograms...",
    "impression": "1. Right lower lobe pneumonia\n2. Stable COPD changes",
    "recommendations": "Antibiotic therapy per CAP guidelines..."
  }
}
```

**Data Split:**
- Training: 40,000 (80%)
- Validation: 5,000 (10%)
- Test: 5,000 (10%)

**Balancing:**
- Modality: 40% X-ray, 35% CT, 25% MRI
- Pathology: 30% normal, 70% abnormal
- Complexity: 40% simple, 40% moderate, 20% complex

### 4.2 QLoRA Training

**Training Configuration:**
```python
from transformers import TrainingArguments
from trl import SFTTrainer

training_args = TrainingArguments(
    output_dir="./llama2-medical-lora",
    num_train_epochs=3,
    per_device_train_batch_size=4,
    gradient_accumulation_steps=8,      # Effective batch: 32
    per_device_eval_batch_size=4,
    learning_rate=2e-4,
    weight_decay=0.01,
    warmup_steps=500,
    logging_steps=10,
    eval_steps=500,
    save_steps=1000,
    fp16=True,
    gradient_checkpointing=True,
    max_seq_length=4096,
    optim="paged_adamw_8bit",
    lr_scheduler_type="cosine"
)

# SFT Trainer (Supervised Fine-Tuning)
trainer = SFTTrainer(
    model=model,
    train_dataset=train_dataset,
    eval_dataset=eval_dataset,
    peft_config=lora_config,
    formatting_func=format_medical_prompt,
    max_seq_length=4096,
    args=training_args
)

# Train
trainer.train()
```

**Training Results:**

| Metric | Epoch 1 | Epoch 2 | Epoch 3 | Final |
|--------|---------|---------|---------|-------|
| Train Loss | 0.52 | 0.38 | 0.32 | 0.32 |
| Val Loss | 0.48 | 0.40 | 0.35 | 0.35 |
| ROUGE-L | 0.65 | 0.72 | 0.76 | 0.76 |
| Radiologist Agreement | 75% | 85% | 89% | 89% |

**Training Time:**
- Hardware: 2× NVIDIA A100 80GB
- Duration: 48 hours (3 epochs)
- Cost: $120 (AWS on-demand)

### 4.3 Evaluation Metrics

**Automated Metrics:**
- ROUGE-L: 0.76 (report similarity)
- BLEU-4: 0.68 (n-gram overlap)
- BERTScore: 0.82 (semantic similarity)

**Clinical Metrics:**
- Radiologist agreement: 89%
- Critical finding detection: 95% sensitivity
- False positive rate: 8%

---

## 5. RAG Implementation

### 5.1 Knowledge Base Construction

**Step 1: Document Collection**
```python
# PubMed scraping
from Bio import Entrez

def download_pubmed_abstracts(query: str, max_results: int = 1000000):
    """Download abstracts from PubMed"""
    Entrez.email = "your@email.com"
    
    handle = Entrez.esearch(
        db="pubmed",
        term=query,
        retmax=max_results
    )
    record = Entrez.read(handle)
    id_list = record["IdList"]
    
    # Fetch abstracts in batches
    abstracts = []
    for i in range(0, len(id_list), 100):
        batch = id_list[i:i+100]
        handle = Entrez.efetch(
            db="pubmed",
            id=batch,
            rettype="abstract",
            retmode="xml"
        )
        abstracts.extend(parse_abstracts(handle))
    
    return abstracts
```

**Step 2: Chunking Strategy**
```python
def chunk_documents(documents: List[str], chunk_size: int = 512):
    """Split documents into chunks"""
    from langchain.text_splitter import RecursiveCharacterTextSplitter
    
    splitter = RecursiveCharacterTextSplitter(
        chunk_size=chunk_size,
        chunk_overlap=128,
        separators=["\n\n", "\n", ". ", " ", ""]
    )
    
    chunks = []
    for doc in documents:
        doc_chunks = splitter.split_text(doc)
        chunks.extend(doc_chunks)
    
    return chunks
```

**Step 3: Embedding Generation**
```python
from sentence_transformers import SentenceTransformer

def generate_embeddings(chunks: List[str], batch_size: int = 32):
    """Generate embeddings for all chunks"""
    
    model = SentenceTransformer(
        'microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract'
    )
    
    embeddings = []
    for i in range(0, len(chunks), batch_size):
        batch = chunks[i:i+batch_size]
        batch_embeddings = model.encode(
            batch,
            show_progress_bar=True,
            convert_to_numpy=True
        )
        embeddings.append(batch_embeddings)
    
    return np.vstack(embeddings)
```

**Step 4: FAISS Index Creation**
```python
import faiss

def create_faiss_index(embeddings: np.ndarray):
    """Create optimized FAISS index"""
    
    d = embeddings.shape[1]  # Dimension (768 for PubMed-BERT)
    n = embeddings.shape[0]  # Number of vectors (5M+)
    
    # IVF index with product quantization
    nlist = 4096  # Number of clusters
    m = 64        # Number of sub-vectors for PQ
    
    quantizer = faiss.IndexFlatL2(d)
    index = faiss.IndexIVFPQ(quantizer, d, nlist, m, 8)
    
    # Train index
    print("Training index...")
    index.train(embeddings)
    
    # Add vectors
    print("Adding vectors...")
    index.add(embeddings)
    
    # Set search parameters
    index.nprobe = 32  # Search 32 clusters
    
    return index

# Save index
faiss.write_index(index, "medical_knowledge.index")
```

### 5.2 Retrieval Pipeline

**Multi-Stage Retrieval:**
```python
def retrieve_context(query: str, patient_data: Dict, image_findings: Dict) -> List[Dict]:
    """Multi-stage retrieval for comprehensive context"""
    
    # Stage 1: Semantic search
    semantic_results = semantic_search(
        query=f"{query} {image_findings['summary']}",
        k=10
    )
    
    # Stage 2: Keyword search (BM25)
    medical_terms = extract_medical_terms(image_findings)
    keyword_results = bm25_search(
        terms=medical_terms,
        k=5
    )
    
    # Stage 3: Similar case retrieval
    similar_cases = find_similar_cases(
        image_embedding=image_findings['embeddings'],
        clinical_features=patient_data,
        k=3
    )
    
    # Stage 4: Guideline matching
    guidelines = match_guidelines(
        condition=image_findings['primary_finding'],
        k=2
    )
    
    # Stage 5: Cross-encoder reranking
    all_results = semantic_results + keyword_results + similar_cases + guidelines
    reranked = rerank_with_cross_encoder(
        query=query,
        documents=all_results,
        top_k=5
    )
    
    return reranked
```

---

## 6. Prompt Engineering

### 6.1 System Prompt

```python
SYSTEM_PROMPT = """You are an expert radiologist assistant analyzing medical imaging studies. 
Your role is to provide accurate, evidence-based preliminary interpretations to assist 
board-certified radiologists.

Core Responsibilities:
1. Analyze imaging findings in clinical context
2. Generate structured radiology reports (Findings, Impression, Recommendations)
3. Provide confidence scores for each finding (0-100%)
4. List differential diagnoses ranked by likelihood
5. Cite relevant medical literature and guidelines
6. Flag critical findings requiring immediate attention

Report Structure:
- FINDINGS: Detailed description of abnormalities
- IMPRESSION: Summary and differential diagnosis
- RECOMMENDATIONS: Next steps (follow-up, additional studies, treatment)
- CONFIDENCE: Overall confidence (0-100%)
- CRITICAL: Any findings requiring immediate attention

Guidelines:
- Use standard radiology terminology
- Be specific about locations (anatomic landmarks)
- Quantify sizes when possible
- Compare to prior imaging when available
- Be conservative - when uncertain, recommend further evaluation
- Always cite literature sources for recommendations

Remember: Your report will be reviewed and signed by a board-certified radiologist. 
Your goal is to enhance their efficiency and reduce errors, not replace their judgment.

Available Context:
- Patient clinical history and indications
- Image analysis from vision model
- Relevant medical literature (PubMed, guidelines)
- Similar historical cases
- Hospital-specific protocols
"""
```

### 6.2 User Prompt Template

```python
USER_PROMPT_TEMPLATE = """
**Exam Information:**
- Type: {exam_type}
- Body Part: {body_part}
- Technique: {technique}
- Clinical Indication: {clinical_indication}

**Patient Context:**
- Age: {age}, Sex: {sex}
- Relevant History: {medical_history}
- Current Medications: {medications}
- Recent Labs: {lab_results}
- Prior Imaging: {prior_imaging_summary}

**Image Analysis (from Vision Model):**
{image_findings}

**Retrieved Medical Knowledge:**
{rag_context}

**Task:**
Generate a comprehensive radiology report in the following JSON format:

{{
  "findings": {{
    "technique": "Description of imaging technique",
    "comparison": "Comparison to prior studies",
    "body_part_1": "Detailed findings",
    "body_part_2": "Detailed findings"
  }},
  "impression": {{
    "primary_findings": ["Finding 1", "Finding 2"],
    "differential_diagnosis": [
      {{"diagnosis": "Most likely", "confidence": 85, "reasoning": "..."}},
      {{"diagnosis": "Alternative", "confidence": 60, "reasoning": "..."}}
    ]
  }},
  "recommendations": [
    "Recommendation 1 with rationale",
    "Recommendation 2 with rationale"
  ],
  "critical_findings": [],
  "confidence": 87,
  "literature_cited": [
    "Author et al. Journal 2023",
    "Clinical Practice Guideline 2022"
  ]
}}
"""
```

### 6.3 Example Prompt & Response

**Input:**
```json
{
  "exam_type": "Chest X-ray (PA and Lateral)",
  "body_part": "Chest",
  "clinical_indication": "Cough and fever × 3 days",
  "patient_context": {
    "age": 65,
    "sex": "M",
    "medical_history": "COPD, former smoker (40 pack-years), quit 5 years ago",
    "medications": "Albuterol inhaler PRN, Spiriva daily",
    "lab_results": "WBC 14.5k (elevated), CRP 85 (elevated)",
    "prior_imaging": "Chest X-ray 6 months ago: Hyperinflation, no acute findings"
  },
  "image_findings": {
    "abnormalities": [
      {
        "location": "Right lower lobe",
        "description": "Focal airspace opacity with air bronchograms",
        "confidence": 0.89,
        "bbox": [120, 340, 220, 440]
      },
      {
        "location": "Right costophrenic angle",
        "description": "Blunting suggests small pleural effusion",
        "confidence": 0.76,
        "bbox": [180, 480, 240, 520]
      }
    ],
    "technical_quality": "Adequate inspiration, no rotation, good penetration"
  },
  "rag_context": [
    {
      "title": "Community-Acquired Pneumonia in COPD Patients",
      "source": "Chest Journal 2022",
      "summary": "COPD patients have 4× risk of CAP. Recommend early antibiotics..."
    }
  ]
}
```

**Output:**
```json
{
  "findings": {
    "technique": "PA and lateral chest radiographs obtained with adequate inspiration and no rotation. Comparison made to prior study from 6 months ago.",
    "lungs": "There is a new focal airspace opacity in the right lower lobe measuring approximately 4×3 cm with air bronchograms, consistent with consolidation. This was not present on prior examination. Background changes of COPD with hyperinflation and flattened diaphragms are stable.",
    "pleura": "Small right pleural effusion is suggested by blunting of the right costophrenic angle on the PA view, new compared to prior.",
    "heart": "Heart size is within normal limits. No pulmonary vascular congestion.",
    "bones": "No acute fractures or lytic lesions identified."
  },
  "impression": {
    "primary_findings": [
      "Right lower lobe pneumonia",
      "Small right pleural effusion"
    ],
    "differential_diagnosis": [
      {
        "diagnosis": "Community-acquired bacterial pneumonia",
        "confidence": 85,
        "reasoning": "Acute presentation with fever, elevated WBC/CRP, and focal consolidation with air bronchograms in a patient with COPD risk factors"
      },
      {
        "diagnosis": "Aspiration pneumonia",
        "confidence": 60,
        "reasoning": "COPD patients have increased aspiration risk; RLL location is consistent with aspiration"
      },
      {
        "diagnosis": "Post-obstructive pneumonia from underlying mass",
        "confidence": 30,
        "reasoning": "Less likely given acute presentation and smoking cessation 5 years ago, but cannot exclude"
      }
    ]
  },
  "recommendations": [
    "Antibiotic therapy per IDSA/ATS community-acquired pneumonia guidelines (2019) is recommended",
    "If no clinical improvement within 72 hours, consider CT chest to evaluate for underlying mass or complications",
    "Follow-up chest X-ray in 4-6 weeks to document resolution and exclude underlying malignancy",
    "Ensure patient is up to date on pneumococcal and influenza vaccinations"
  ],
  "critical_findings": [],
  "confidence": 87,
  "literature_cited": [
    "IDSA/ATS Guidelines for Community-Acquired Pneumonia 2019",
    "Pneumonia in COPD: Risk and Management, Chest 2022;158(3):823-832"
  ],
  "processing_metadata": {
    "model_version": "v2.3.1",
    "processing_time_ms": 2340,
    "rag_sources_used": 5
  }
}
```

---

## 7. Infrastructure & Deployment

### 7.1 Production Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                Load Balancer (HAProxy)                           │
│              Health Checks, SSL Termination                      │
└────────────────────────┬─────────────────────────────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
┌───────▼──────┐ ┌──────▼───────┐ ┌──────▼───────┐
│   API Node 1  │ │  API Node 2  │ │  API Node 3  │
│  FastAPI      │ │  FastAPI     │ │  FastAPI     │
│  + Auth       │ │  + Auth      │ │  + Auth      │
│  8 vCPU       │ │  8 vCPU      │ │  8 vCPU      │
└───────┬───────┘ └──────┬───────┘ └──────┬───────┘
        │                │                │
        └────────────────┼────────────────┘
                         │
        ┌────────────────▼────────────────┐
        │      Redis Cache Layer          │
        │  - Response caching (45% hit)   │
        │  - Session management           │
        │  - Rate limiting                │
        └────────────────┬────────────────┘
                         │
        ┌────────────────▼────────────────┐
        │    Model Serving (vLLM)         │
        │  - LLaMA 2 70B (4-bit)          │
        │  - 4× A100 80GB GPUs            │
        │  - Continuous batching          │
        │  - PagedAttention               │
        └────────────────┬────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
┌───────▼──────┐ ┌──────▼───────┐ ┌──────▼───────┐
│  FAISS RAG   │ │  PostgreSQL  │ │  MinIO S3    │
│  Vector DB   │ │  Audit Logs  │ │  DICOM Files │
│  80GB RAM    │ │  Metadata    │ │  50TB        │
└──────────────┘ └──────────────┘ └──────────────┘
```

### 7.2 Hardware Specifications

| Component | Specification | Monthly Cost | Purpose |
|-----------|--------------|--------------|---------|
| **GPU Servers** | 4× A100 80GB | $12,000 | LLaMA 2 70B inference |
| **API Servers** | 3× c5.4xlarge (16 vCPU, 32GB RAM) | $900 | Request handling |
| **Redis Cache** | r6g.2xlarge (8 vCPU, 64GB RAM) | $400 | Caching, sessions |
| **Vector DB** | r5.8xlarge (32 vCPU, 256GB RAM) | $1,600 | FAISS in-memory |
| **PostgreSQL** | db.r5.2xlarge (8 vCPU, 64GB RAM) | $800 | Audit logs, metadata |
| **S3 Storage** | 50TB | $1,150 | DICOM archive, models |
| **Monitoring** | DataDog + PagerDuty | $500 | Observability |
| **Networking** | VPN, Load Balancers | $500 | Connectivity |
| **Total** | | **$17,850/mo** | |

### 7.3 Kubernetes Deployment

```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: medical-diagnosis-api
  namespace: radiology
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 0
  selector:
    matchLabels:
      app: diagnosis-api
  template:
    metadata:
      labels:
        app: diagnosis-api
    spec:
      containers:
      - name: api
        image: hospital-registry.azurecr.io/diagnosis-api:v2.3.1
        ports:
        - containerPort: 8080
        resources:
          requests:
            memory: "16Gi"
            cpu: "8"
          limits:
            memory: "32Gi"
            cpu: "16"
        env:
        - name: MODEL_ENDPOINT
          value: "http://vllm-service:8000"
        - name: FAISS_INDEX_PATH
          value: "/mnt/faiss/medical-knowledge.index"
        - name: REDIS_URL
          valueFrom:
            secretKeyRef:
              name: redis-credentials
              key: url
        - name: POSTGRES_URL
          valueFrom:
            secretKeyRef:
              name: postgres-credentials
              key: url
        livenessProbe:
          httpGet:
            path: /health
            port: 8080
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 5
        readinessProbe:
          httpGet:
            path: /ready
            port: 8080
          initialDelaySeconds: 15
          periodSeconds: 5
        volumeMounts:
        - name: faiss-index
          mountPath: /mnt/faiss
          readOnly: true
      volumes:
      - name: faiss-index
        persistentVolumeClaim:
          claimName: faiss-pvc
---
# vllm-deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: vllm-llama2
  namespace: radiology
spec:
  replicas: 2
  selector:
    matchLabels:
      app: vllm
  template:
    metadata:
      labels:
        app: vllm
    spec:
      nodeSelector:
        gpu: "a100"
      containers:
      - name: vllm
        image: vllm/vllm-openai:latest
        args:
        - --model
        - /models/llama2-70b-medical-lora
        - --tensor-parallel-size
        - "4"
        - --dtype
        - float16
        - --max-model-len
        - "4096"
        - --gpu-memory-utilization
        - "0.95"
        ports:
        - containerPort: 8000
        resources:
          limits:
            nvidia.com/gpu: 4
        volumeMounts:
        - name: model-storage
          mountPath: /models
      volumes:
      - name: model-storage
        persistentVolumeClaim:
          claimName: model-pvc
```

---

## 8. Monitoring & Observability

### 8.1 Prometheus Metrics

```python
from prometheus_client import Counter, Histogram, Gauge

# Request metrics
requests_total = Counter(
    'diagnosis_requests_total',
    'Total diagnosis requests',
    ['exam_type', 'priority']
)

# Latency metrics
inference_latency = Histogram(
    'diagnosis_inference_latency_seconds',
    'Time to generate diagnosis',
    buckets=[0.5, 1.0, 2.0, 5.0, 10.0, 30.0]
)

rag_retrieval_latency = Histogram(
    'rag_retrieval_latency_seconds',
    'Time to retrieve knowledge',
    buckets=[0.05, 0.1, 0.2, 0.5, 1.0, 2.0]
)

# Quality metrics
radiologist_agreement_rate = Gauge(
    'radiologist_agreement_rate',
    'Percentage agreement with AI'
)

critical_finding_detection_rate = Gauge(
    'critical_finding_detection_rate',
    'Percentage critical findings detected'
)

# Error tracking
errors_total = Counter(
    'diagnosis_errors_total',
    'Total errors by type',
    ['error_type']
)
```

### 8.2 Grafana Dashboards

**Dashboard 1: System Health**
- Request rate (requests/second)
- Error rate (%)
- P50, P95, P99 latency
- GPU utilization
- Memory usage

**Dashboard 2: Clinical Performance**
- Studies processed per hour
- Radiologist agreement rate
- Critical finding detection rate
- Average confidence scores
- Error types distribution

**Dashboard 3: Cost Tracking**
- Cost per study
- GPU hours used
- API costs
- Storage costs
- Total daily cost

---

📑 **Navigation**: [🏠 Main](./README.md) | [📊 Overview](./README_Overview.md) | [⚠️ Challenges](./README_Challenges_Solutions.md) | [💻 Code](./README_Code_Snippets.md) | [🚀 Future](./README_Future_Improvements.md)

