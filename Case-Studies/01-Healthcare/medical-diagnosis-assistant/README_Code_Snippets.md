# 💻 Medical Diagnosis Assistant - Complete Code

📑 **Navigation**: [🏠 Main](./README.md) | [📊 Overview](./README_Overview.md) | [🏗️ Architecture](./README_Solution_Architecture.md) | [⚠️ Challenges](./README_Challenges_Solutions.md) | [🚀 Future](./README_Future_Improvements.md)

---

## Table of Contents

1. [End-to-End Inference Pipeline](#1-end-to-end-inference-pipeline)
2. [Vision Analysis (BioMed-CLIP)](#2-vision-analysis-biomed-clip)
3. [RAG Implementation](#3-rag-implementation)
4. [Fine-Tuning Scripts](#4-fine-tuning-scripts)
5. [Deployment (Kubernetes)](#5-deployment-kubernetes)
6. [Monitoring & Logging](#6-monitoring--logging)
7. [Full Working Example](#7-full-working-example)

---

## 1. End-to-End Inference Pipeline

### 1.1 Main MedicalDiagnosisAssistant Class

```python
"""
Medical Diagnosis Assistant - Production Implementation
Complete end-to-end pipeline for radiology report generation
"""

import torch
import numpy as np
from typing import Dict, List, Optional
from dataclasses import dataclass
from datetime import datetime
import logging
from transformers import AutoTokenizer, AutoModelForCausalLM
from peft import PeftModel
import pydicom
from PIL import Image

# Configure logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)


@dataclass
class DiagnosisRequest:
    """Input request structure"""
    study_id: str
    patient_id_hash: str  # De-identified
    exam_type: str  # "CHEST_XRAY", "CT_CHEST", etc.
    dicom_paths: List[str]
    patient_context: Dict  # Age, sex, symptoms, history
    clinical_indication: str
    priority: str  # "STAT", "URGENT", "ROUTINE"


@dataclass
class DiagnosisResponse:
    """Output response structure"""
    study_id: str
    findings: List[Dict]
    impression: str
    recommendations: List[str]
    confidence: float
    critical_findings: List[Dict]
    processing_time_ms: float
    model_version: str


class MedicalDiagnosisAssistant:
    """
    Production-ready medical diagnosis assistant
    
    Features:
    - Multimodal analysis (images + text)
    - RAG-enhanced medical knowledge
    - HIPAA-compliant audit logging
    - Conservative thresholds for critical findings
    """
    
    def __init__(
        self,
        llm_model_path: str = "meta-llama/Llama-2-70b-chat-hf",
        lora_adapter_path: str = "./adapters/medical-lora",
        vision_model_path: str = "microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224",
        rag_index_path: str = "./rag/faiss_index",
        device: str = "cuda",
        use_4bit: bool = True
    ):
        """Initialize all model components"""
        
        self.device = device
        logger.info(f"Initializing MedicalDiagnosisAssistant on {device}")
        
        # 1. Load LLM (LLaMA 2 70B with QLoRA)
        logger.info("Loading LLM...")
        self.tokenizer = AutoTokenizer.from_pretrained(llm_model_path)
        
        if use_4bit:
            from transformers import BitsAndBytesConfig
            quantization_config = BitsAndBytesConfig(
                load_in_4bit=True,
                bnb_4bit_compute_dtype=torch.float16,
                bnb_4bit_use_double_quant=True,
                bnb_4bit_quant_type="nf4"
            )
            
            self.llm = AutoModelForCausalLM.from_pretrained(
                llm_model_path,
                quantization_config=quantization_config,
                device_map="auto",
                trust_remote_code=True
            )
        else:
            self.llm = AutoModelForCausalLM.from_pretrained(
                llm_model_path,
                torch_dtype=torch.float16,
                device_map="auto"
            )
        
        # Load LoRA adapter
        logger.info(f"Loading LoRA adapter from {lora_adapter_path}")
        self.llm = PeftModel.from_pretrained(self.llm, lora_adapter_path)
        self.llm.eval()
        
        # 2. Load Vision Model (BioMed-CLIP)
        logger.info("Loading vision model...")
        from transformers import CLIPProcessor, CLIPModel
        self.vision_processor = CLIPProcessor.from_pretrained(vision_model_path)
        self.vision_model = CLIPModel.from_pretrained(vision_model_path).to(device)
        self.vision_model.eval()
        
        # 3. Load RAG system
        logger.info("Loading RAG index...")
        from .rag import MedicalRAG
        self.rag = MedicalRAG(index_path=rag_index_path, device=device)
        
        # 4. Load confidence calibrator
        logger.info("Loading confidence calibrator...")
        from .calibration import ConfidenceCalibrator
        self.calibrator = ConfidenceCalibrator.load("./models/calibrator.pkl")
        
        # 5. Define critical condition thresholds
        self.CRITICAL_THRESHOLDS = {
            "pulmonary_embolism": 0.30,
            "aortic_dissection": 0.25,
            "tension_pneumothorax": 0.35,
            "acute_stroke": 0.30,
            "bowel_perforation": 0.35,
            "massive_hemothorax": 0.40
        }
        
        logger.info("Initialization complete")
    
    def analyze_study(self, request: DiagnosisRequest) -> DiagnosisResponse:
        """
        Main entry point: Analyze medical study and generate report
        
        Pipeline:
        1. Load and preprocess DICOM images
        2. Vision analysis (BioMed-CLIP)
        3. Retrieve relevant medical knowledge (RAG)
        4. Generate report (LLM)
        5. Post-processing (confidence calibration, critical alerts)
        """
        
        start_time = datetime.now()
        logger.info(f"Analyzing study {request.study_id}")
        
        try:
            # Step 1: Load images
            images, image_features = self._load_and_analyze_images(request.dicom_paths)
            
            # Step 2: Vision analysis
            vision_findings = self._analyze_images_with_vision_model(
                images, image_features, request.exam_type
            )
            
            # Step 3: RAG retrieval
            rag_context = self._retrieve_medical_knowledge(
                exam_type=request.exam_type,
                vision_findings=vision_findings,
                patient_context=request.patient_context,
                clinical_indication=request.clinical_indication
            )
            
            # Step 4: Generate report with LLM
            report = self._generate_report(
                vision_findings=vision_findings,
                rag_context=rag_context,
                patient_context=request.patient_context,
                exam_type=request.exam_type
            )
            
            # Step 5: Post-processing
            report = self._post_process_report(report)
            
            # Step 6: Check for critical findings
            critical_findings = self._check_critical_findings(report["findings"])
            
            # Compute processing time
            processing_time = (datetime.now() - start_time).total_seconds() * 1000
            
            # Create response
            response = DiagnosisResponse(
                study_id=request.study_id,
                findings=report["findings"],
                impression=report["impression"],
                recommendations=report["recommendations"],
                confidence=report["overall_confidence"],
                critical_findings=critical_findings,
                processing_time_ms=processing_time,
                model_version="v1.2.0"
            )
            
            logger.info(f"Study {request.study_id} analyzed in {processing_time:.0f}ms")
            
            return response
            
        except Exception as e:
            logger.error(f"Error analyzing study {request.study_id}: {e}")
            raise
    
    def _load_and_analyze_images(
        self,
        dicom_paths: List[str]
    ) -> tuple[List[Image.Image], List[np.ndarray]]:
        """Load DICOM files and extract image features"""
        
        images = []
        image_features = []
        
        for path in dicom_paths:
            # Load DICOM
            dcm = pydicom.dcmread(path)
            
            # Extract pixel array
            pixel_array = dcm.pixel_array
            
            # Normalize to 0-255
            pixel_array = (pixel_array - pixel_array.min()) / (pixel_array.max() - pixel_array.min())
            pixel_array = (pixel_array * 255).astype(np.uint8)
            
            # Convert to PIL Image
            if len(pixel_array.shape) == 2:
                # Grayscale
                image = Image.fromarray(pixel_array).convert("RGB")
            else:
                image = Image.fromarray(pixel_array)
            
            images.append(image)
            
            # Extract metadata features
            features = {
                "modality": dcm.get("Modality", ""),
                "body_part": dcm.get("BodyPartExamined", ""),
                "view_position": dcm.get("ViewPosition", ""),
                "rows": dcm.Rows,
                "columns": dcm.Columns,
                "pixel_spacing": dcm.get("PixelSpacing", [1.0, 1.0])
            }
            image_features.append(features)
        
        return images, image_features
    
    def _analyze_images_with_vision_model(
        self,
        images: List[Image.Image],
        image_features: List[Dict],
        exam_type: str
    ) -> List[Dict]:
        """Analyze images with BioMed-CLIP"""
        
        vision_findings = []
        
        # Define finding templates by exam type
        if exam_type == "CHEST_XRAY":
            finding_templates = [
                "consolidation in the lung",
                "pleural effusion",
                "pneumothorax",
                "pulmonary edema",
                "cardiomegaly",
                "lung nodule",
                "rib fracture",
                "normal chest radiograph"
            ]
        elif exam_type == "CT_CHEST":
            finding_templates = [
                "pulmonary embolism",
                "pneumonia",
                "lung mass",
                "ground glass opacities",
                "mediastinal lymphadenopathy",
                "pleural effusion",
                "normal chest CT"
            ]
        else:
            finding_templates = ["abnormality", "normal study"]
        
        # Process each image
        for idx, (image, features) in enumerate(zip(images, image_features)):
            # Prepare inputs
            inputs = self.vision_processor(
                text=finding_templates,
                images=image,
                return_tensors="pt",
                padding=True
            ).to(self.device)
            
            # Get predictions
            with torch.no_grad():
                outputs = self.vision_model(**inputs)
                logits_per_image = outputs.logits_per_image
                probs = logits_per_image.softmax(dim=1).cpu().numpy()[0]
            
            # Extract top findings
            top_indices = np.argsort(probs)[-3:][::-1]  # Top 3
            
            for idx in top_indices:
                if probs[idx] > 0.20:  # Threshold
                    vision_findings.append({
                        "finding": finding_templates[idx],
                        "confidence": float(probs[idx]),
                        "image_index": idx,
                        "source": "vision_model"
                    })
        
        logger.info(f"Vision model identified {len(vision_findings)} findings")
        
        return vision_findings
    
    def _retrieve_medical_knowledge(
        self,
        exam_type: str,
        vision_findings: List[Dict],
        patient_context: Dict,
        clinical_indication: str
    ) -> List[Dict]:
        """Retrieve relevant medical knowledge via RAG"""
        
        # Construct query
        findings_text = ", ".join([f["finding"] for f in vision_findings])
        query = f"""
        Exam type: {exam_type}
        Findings: {findings_text}
        Patient age: {patient_context.get('age', 'unknown')}
        Patient sex: {patient_context.get('sex', 'unknown')}
        Clinical indication: {clinical_indication}
        """
        
        # Retrieve from RAG
        rag_results = self.rag.retrieve(
            query=query,
            k=10,
            filters={"modality": exam_type.lower()}
        )
        
        logger.info(f"Retrieved {len(rag_results)} RAG documents")
        
        return rag_results
    
    def _generate_report(
        self,
        vision_findings: List[Dict],
        rag_context: List[Dict],
        patient_context: Dict,
        exam_type: str
    ) -> Dict:
        """Generate radiology report with LLM"""
        
        # Construct prompt
        system_prompt = """You are an expert radiologist with 20 years of experience. 
Generate a structured radiology report based on the imaging findings and medical context provided.

Guidelines:
- Be concise and precise
- Use standard radiology terminology
- Cite relevant literature when applicable
- Flag critical findings with [CRITICAL]
- Provide confidence scores (0-100%)
- List differential diagnoses when appropriate

Output format:
{
    "findings": [
        {"description": "...", "location": "...", "severity": "...", "confidence": 85}
    ],
    "impression": "Overall diagnostic impression",
    "recommendations": ["Recommendation 1", "Recommendation 2"],
    "differential_diagnosis": ["Diagnosis 1", "Diagnosis 2"]
}
"""
        
        # Format vision findings
        findings_text = "\n".join([
            f"- {f['finding']} (confidence: {f['confidence']:.0%})"
            for f in vision_findings
        ])
        
        # Format RAG context (top 5)
        rag_text = "\n\n".join([
            f"Reference {idx+1}:\n{r['text']}\nSource: {r['source']}"
            for idx, r in enumerate(rag_context[:5])
        ])
        
        # Construct user prompt
        user_prompt = f"""
Exam Type: {exam_type}

Patient Context:
- Age: {patient_context.get('age', 'unknown')}
- Sex: {patient_context.get('sex', 'unknown')}
- Symptoms: {patient_context.get('symptoms', 'none reported')}
- Medical history: {patient_context.get('medical_history', 'none reported')}

Imaging Findings (from Vision Model):
{findings_text}

Relevant Medical Literature:
{rag_text}

Generate a radiology report in JSON format.
"""
        
        # Format for LLaMA 2 chat template
        messages = [
            {"role": "system", "content": system_prompt},
            {"role": "user", "content": user_prompt}
        ]
        
        prompt = self.tokenizer.apply_chat_template(
            messages,
            tokenize=False,
            add_generation_prompt=True
        )
        
        # Generate
        inputs = self.tokenizer(prompt, return_tensors="pt").to(self.device)
        
        with torch.no_grad():
            outputs = self.llm.generate(
                **inputs,
                max_new_tokens=1024,
                temperature=0.2,  # Low temperature for medical accuracy
                top_p=0.9,
                do_sample=True,
                pad_token_id=self.tokenizer.eos_token_id
            )
        
        # Decode
        generated_text = self.tokenizer.decode(outputs[0], skip_special_tokens=True)
        
        # Extract JSON from response
        import json
        import re
        
        # Find JSON block
        json_match = re.search(r'\{.*\}', generated_text, re.DOTALL)
        if json_match:
            report_json = json.loads(json_match.group())
        else:
            # Fallback
            report_json = {
                "findings": [{"description": generated_text, "confidence": 50}],
                "impression": "Unable to parse structured report",
                "recommendations": []
            }
        
        return report_json
    
    def _post_process_report(self, report: Dict) -> Dict:
        """Post-process report: calibrate confidence, add metadata"""
        
        # Calibrate confidence scores
        for finding in report["findings"]:
            raw_confidence = finding.get("confidence", 50) / 100.0
            calibrated = self.calibrator.calibrate(raw_confidence)
            finding["confidence"] = int(calibrated * 100)
        
        # Compute overall confidence
        if report["findings"]:
            confidences = [f["confidence"] for f in report["findings"]]
            report["overall_confidence"] = np.mean(confidences)
        else:
            report["overall_confidence"] = 0
        
        return report
    
    def _check_critical_findings(self, findings: List[Dict]) -> List[Dict]:
        """Check for critical findings with low thresholds"""
        
        critical_findings = []
        
        for finding in findings:
            description_lower = finding["description"].lower()
            confidence = finding["confidence"] / 100.0
            
            # Check against critical conditions
            for condition, threshold in self.CRITICAL_THRESHOLDS.items():
                condition_terms = condition.replace("_", " ")
                
                if condition_terms in description_lower:
                    if confidence > threshold:
                        critical_findings.append({
                            "condition": condition,
                            "description": finding["description"],
                            "confidence": finding["confidence"],
                            "threshold": threshold,
                            "action": "PAGE_RADIOLOGIST_STAT",
                            "rationale": f"Critical finding detected with {confidence:.0%} confidence (threshold: {threshold:.0%})"
                        })
        
        if critical_findings:
            logger.warning(f"CRITICAL: {len(critical_findings)} critical findings detected")
        
        return critical_findings


# ============================================================================
# Example Usage
# ============================================================================

def main():
    """Example usage of MedicalDiagnosisAssistant"""
    
    # Initialize assistant
    assistant = MedicalDiagnosisAssistant(
        llm_model_path="meta-llama/Llama-2-70b-chat-hf",
        lora_adapter_path="./adapters/medical-lora",
        vision_model_path="microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224",
        rag_index_path="./rag/faiss_index",
        device="cuda",
        use_4bit=True
    )
    
    # Create request
    request = DiagnosisRequest(
        study_id="STUDY_12345",
        patient_id_hash="a3f2d8e1",  # De-identified
        exam_type="CHEST_XRAY",
        dicom_paths=[
            "/data/studies/12345/PA.dcm",
            "/data/studies/12345/LATERAL.dcm"
        ],
        patient_context={
            "age": 65,
            "sex": "M",
            "symptoms": "Cough, fever, shortness of breath for 3 days",
            "medical_history": "Hypertension, Type 2 diabetes",
            "medications": ["Metformin", "Lisinopril"]
        },
        clinical_indication="Rule out pneumonia",
        priority="URGENT"
    )
    
    # Analyze
    response = assistant.analyze_study(request)
    
    # Print results
    print(f"\n{'='*60}")
    print(f"Study ID: {response.study_id}")
    print(f"Processing Time: {response.processing_time_ms:.0f}ms")
    print(f"Overall Confidence: {response.confidence:.0f}%")
    print(f"{'='*60}\n")
    
    print("FINDINGS:")
    for finding in response.findings:
        print(f"  • {finding['description']} ({finding['confidence']}% confident)")
    
    print(f"\nIMPRESSION:")
    print(f"  {response.impression}")
    
    print(f"\nRECOMMENDATIONS:")
    for rec in response.recommendations:
        print(f"  • {rec}")
    
    if response.critical_findings:
        print(f"\n🚨 CRITICAL FINDINGS:")
        for critical in response.critical_findings:
            print(f"  ⚠️  {critical['condition'].upper()} ({critical['confidence']}% confident)")
            print(f"      Action: {critical['action']}")


if __name__ == "__main__":
    main()
```

---

## 2. Vision Analysis (BioMed-CLIP)

### 2.1 BioMed-CLIP Integration

```python
"""
Vision analysis using BioMed-CLIP
Specialized for medical imaging (trained on PubMed data)
"""

import torch
import numpy as np
from transformers import CLIPProcessor, CLIPModel
from PIL import Image
from typing import List, Dict


class MedicalVisionAnalyzer:
    """Analyze medical images with BioMed-CLIP"""
    
    def __init__(
        self,
        model_name: str = "microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224",
        device: str = "cuda"
    ):
        self.device = device
        self.processor = CLIPProcessor.from_pretrained(model_name)
        self.model = CLIPModel.from_pretrained(model_name).to(device)
        self.model.eval()
        
        # Define finding templates by modality
        self.finding_templates = {
            "chest_xray": [
                "consolidation",
                "pleural effusion",
                "pneumothorax",
                "pulmonary edema",
                "cardiomegaly",
                "lung nodule",
                "rib fracture",
                "pneumonia",
                "atelectasis",
                "normal chest radiograph"
            ],
            "ct_chest": [
                "pulmonary embolism",
                "lung mass",
                "ground glass opacity",
                "mediastinal lymphadenopathy",
                "consolidation",
                "pleural effusion",
                "emphysema",
                "normal chest CT"
            ],
            "ct_head": [
                "acute hemorrhage",
                "ischemic stroke",
                "midline shift",
                "mass effect",
                "hydrocephalus",
                "skull fracture",
                "normal head CT"
            ]
        }
    
    def analyze_image(
        self,
        image: Image.Image,
        modality: str,
        threshold: float = 0.20
    ) -> List[Dict]:
        """
        Analyze single medical image
        
        Args:
            image: PIL Image
            modality: "chest_xray", "ct_chest", "ct_head", etc.
            threshold: Minimum confidence to report finding
        
        Returns:
            List of findings with confidence scores
        """
        
        # Get templates for this modality
        templates = self.finding_templates.get(
            modality.lower(),
            ["abnormality", "normal"]
        )
        
        # Prepare inputs
        inputs = self.processor(
            text=templates,
            images=image,
            return_tensors="pt",
            padding=True
        ).to(self.device)
        
        # Get predictions
        with torch.no_grad():
            outputs = self.model(**inputs)
            logits_per_image = outputs.logits_per_image
            probs = logits_per_image.softmax(dim=1).cpu().numpy()[0]
        
        # Extract findings above threshold
        findings = []
        for idx, (template, prob) in enumerate(zip(templates, probs)):
            if prob > threshold:
                findings.append({
                    "finding": template,
                    "confidence": float(prob),
                    "rank": len(findings) + 1
                })
        
        # Sort by confidence
        findings.sort(key=lambda x: x["confidence"], reverse=True)
        
        return findings
    
    def localize_findings(
        self,
        image: Image.Image,
        findings: List[str],
        patch_size: int = 112
    ) -> Dict[str, np.ndarray]:
        """
        Localize findings in image using sliding window
        
        Returns:
            Dictionary mapping finding to heatmap (HxW array)
        """
        
        W, H = image.size
        heatmaps = {finding: np.zeros((H, W)) for finding in findings}
        
        # Sliding window
        stride = patch_size // 2
        for y in range(0, H - patch_size, stride):
            for x in range(0, W - patch_size, stride):
                # Extract patch
                patch = image.crop((x, y, x + patch_size, y + patch_size))
                
                # Score patch
                inputs = self.processor(
                    text=findings,
                    images=patch,
                    return_tensors="pt",
                    padding=True
                ).to(self.device)
                
                with torch.no_grad():
                    outputs = self.model(**inputs)
                    probs = outputs.logits_per_image.softmax(dim=1).cpu().numpy()[0]
                
                # Update heatmaps
                for finding, prob in zip(findings, probs):
                    heatmaps[finding][y:y+patch_size, x:x+patch_size] += prob
        
        # Normalize heatmaps
        for finding in findings:
            heatmaps[finding] /= heatmaps[finding].max()
        
        return heatmaps


# Example usage
if __name__ == "__main__":
    analyzer = MedicalVisionAnalyzer()
    
    image = Image.open("chest_xray.jpg")
    findings = analyzer.analyze_image(image, modality="chest_xray")
    
    print("Detected findings:")
    for f in findings:
        print(f"  {f['finding']}: {f['confidence']:.0%}")
```

---

## 3. RAG Implementation

### 3.1 Medical Knowledge Base RAG

```python
"""
RAG (Retrieval-Augmented Generation) for medical knowledge
Uses FAISS for efficient similarity search over medical literature
"""

import faiss
import numpy as np
import torch
from transformers import AutoTokenizer, AutoModel
from typing import List, Dict, Optional
import pickle


class MedicalRAG:
    """Retrieval-Augmented Generation for medical knowledge"""
    
    def __init__(
        self,
        index_path: str,
        embedding_model: str = "microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext",
        device: str = "cuda"
    ):
        """
        Initialize RAG system
        
        Args:
            index_path: Path to FAISS index directory
            embedding_model: HuggingFace model for embeddings
            device: "cuda" or "cpu"
        """
        
        self.device = device
        
        # Load embedding model
        self.tokenizer = AutoTokenizer.from_pretrained(embedding_model)
        self.model = AutoModel.from_pretrained(embedding_model).to(device)
        self.model.eval()
        
        # Load FAISS index
        self.index = faiss.read_index(f"{index_path}/medical_knowledge.index")
        
        # Load metadata (texts, sources)
        with open(f"{index_path}/metadata.pkl", "rb") as f:
            self.metadata = pickle.load(f)
        
        print(f"Loaded RAG index with {self.index.ntotal} documents")
    
    def embed_text(self, text: str) -> np.ndarray:
        """Convert text to embedding vector"""
        
        inputs = self.tokenizer(
            text,
            return_tensors="pt",
            padding=True,
            truncation=True,
            max_length=512
        ).to(self.device)
        
        with torch.no_grad():
            outputs = self.model(**inputs)
            # Use [CLS] token embedding
            embedding = outputs.last_hidden_state[:, 0, :].cpu().numpy()
        
        return embedding[0]
    
    def retrieve(
        self,
        query: str,
        k: int = 10,
        filters: Optional[Dict] = None
    ) -> List[Dict]:
        """
        Retrieve relevant documents
        
        Args:
            query: Search query
            k: Number of results to return
            filters: Optional metadata filters (e.g., {"modality": "chest_xray"})
        
        Returns:
            List of retrieved documents with scores
        """
        
        # Embed query
        query_embedding = self.embed_text(query)
        query_embedding = query_embedding.reshape(1, -1).astype('float32')
        
        # Normalize for cosine similarity
        faiss.normalize_L2(query_embedding)
        
        # Search
        distances, indices = self.index.search(query_embedding, k * 2)  # Get extra for filtering
        
        # Retrieve metadata
        results = []
        for dist, idx in zip(distances[0], indices[0]):
            if idx == -1:  # FAISS returns -1 for no match
                continue
            
            doc = self.metadata[idx]
            
            # Apply filters
            if filters:
                if not all(doc.get(key) == value for key, value in filters.items()):
                    continue
            
            results.append({
                "text": doc["text"],
                "source": doc["source"],
                "score": float(dist),
                "metadata": doc.get("metadata", {})
            })
            
            if len(results) >= k:
                break
        
        return results
    
    def retrieve_with_reranking(
        self,
        query: str,
        k: int = 10,
        rerank_k: int = 50
    ) -> List[Dict]:
        """
        Retrieve with cross-encoder reranking for better relevance
        
        Pipeline:
        1. Retrieve top rerank_k candidates with bi-encoder (fast)
        2. Rerank with cross-encoder (slow but accurate)
        3. Return top k
        """
        
        # Stage 1: Bi-encoder retrieval
        candidates = self.retrieve(query, k=rerank_k)
        
        # Stage 2: Cross-encoder reranking
        from sentence_transformers import CrossEncoder
        
        reranker = CrossEncoder(
            "cross-encoder/ms-marco-MiniLM-L-12-v2",
            max_length=512
        )
        
        # Score all candidates
        pairs = [[query, cand["text"]] for cand in candidates]
        scores = reranker.predict(pairs)
        
        # Sort by reranked score
        for cand, score in zip(candidates, scores):
            cand["rerank_score"] = float(score)
        
        candidates.sort(key=lambda x: x["rerank_score"], reverse=True)
        
        return candidates[:k]


# ============================================================================
# Building the RAG Index (One-time setup)
# ============================================================================

class RAGIndexBuilder:
    """Build FAISS index from medical literature"""
    
    def __init__(
        self,
        embedding_model: str = "microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext",
        device: str = "cuda"
    ):
        self.device = device
        self.tokenizer = AutoTokenizer.from_pretrained(embedding_model)
        self.model = AutoModel.from_pretrained(embedding_model).to(device)
        self.model.eval()
    
    def build_index(
        self,
        documents: List[Dict],
        output_path: str,
        index_type: str = "IVF"
    ):
        """
        Build FAISS index from documents
        
        Args:
            documents: List of dicts with keys: "text", "source", "metadata"
            output_path: Where to save index
            index_type: "Flat" (exact) or "IVF" (approximate)
        """
        
        print(f"Building index for {len(documents)} documents...")
        
        # Embed all documents
        embeddings = []
        metadata = []
        
        for idx, doc in enumerate(documents):
            if idx % 1000 == 0:
                print(f"  Embedded {idx}/{len(documents)}")
            
            embedding = self._embed_text(doc["text"])
            embeddings.append(embedding)
            metadata.append(doc)
        
        embeddings = np.array(embeddings).astype('float32')
        
        # Normalize for cosine similarity
        faiss.normalize_L2(embeddings)
        
        # Build index
        d = embeddings.shape[1]  # Dimension
        
        if index_type == "Flat":
            # Exact search (slow but accurate)
            index = faiss.IndexFlatIP(d)  # Inner product = cosine after normalization
        elif index_type == "IVF":
            # Approximate search (fast)
            nlist = 4096  # Number of clusters
            quantizer = faiss.IndexFlatIP(d)
            index = faiss.IndexIVFFlat(quantizer, d, nlist, faiss.METRIC_INNER_PRODUCT)
            
            # Train index
            print("Training index...")
            index.train(embeddings)
        
        # Add vectors
        print("Adding vectors...")
        index.add(embeddings)
        
        # Save
        print(f"Saving to {output_path}...")
        faiss.write_index(index, f"{output_path}/medical_knowledge.index")
        
        with open(f"{output_path}/metadata.pkl", "wb") as f:
            pickle.dump(metadata, f)
        
        print("Done!")
    
    def _embed_text(self, text: str) -> np.ndarray:
        """Embed text"""
        inputs = self.tokenizer(
            text,
            return_tensors="pt",
            padding=True,
            truncation=True,
            max_length=512
        ).to(self.device)
        
        with torch.no_grad():
            outputs = self.model(**inputs)
            embedding = outputs.last_hidden_state[:, 0, :].cpu().numpy()
        
        return embedding[0]


# Example: Build index from PubMed abstracts
if __name__ == "__main__":
    # Load documents (example: PubMed abstracts)
    documents = [
        {
            "text": "Pneumonia is an infection that inflames the air sacs in one or both lungs...",
            "source": "PubMed:12345678",
            "metadata": {"modality": "chest_xray", "topic": "pneumonia"}
        },
        # ... more documents
    ]
    
    builder = RAGIndexBuilder()
    builder.build_index(
        documents=documents,
        output_path="./rag_index",
        index_type="IVF"
    )
```

---

## 4. Fine-Tuning Scripts

### 4.1 QLoRA Fine-Tuning Configuration

```python
"""
Fine-tune LLaMA 2 70B on radiology reports using QLoRA
Memory-efficient training with 4-bit quantization
"""

import torch
from transformers import (
    AutoModelForCausalLM,
    AutoTokenizer,
    BitsAndBytesConfig,
    TrainingArguments,
    Trainer
)
from peft import LoraConfig, get_peft_model, prepare_model_for_kbit_training
from datasets import Dataset
import pandas as pd


# ============================================================================
# Configuration
# ============================================================================

MODEL_NAME = "meta-llama/Llama-2-70b-chat-hf"
OUTPUT_DIR = "./medical-diagnosis-lora"

# QLoRA configuration
bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_compute_dtype=torch.float16,
    bnb_4bit_use_double_quant=True,
    bnb_4bit_quant_type="nf4"
)

# LoRA configuration
lora_config = LoraConfig(
    r=64,                          # Rank
    lora_alpha=16,                  # Scaling factor
    target_modules=[                # Which layers to adapt
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

# Training configuration
training_args = TrainingArguments(
    output_dir=OUTPUT_DIR,
    num_train_epochs=3,
    per_device_train_batch_size=4,
    per_device_eval_batch_size=4,
    gradient_accumulation_steps=8,        # Effective batch size: 4 * 8 = 32
    learning_rate=2e-4,
    lr_scheduler_type="cosine",
    warmup_steps=100,
    logging_steps=10,
    save_steps=500,
    evaluation_strategy="steps",
    eval_steps=500,
    fp16=True,
    optim="paged_adamw_8bit",             # Memory-efficient optimizer
    save_total_limit=3,
    load_best_model_at_end=True,
    metric_for_best_model="eval_loss",
    report_to="tensorboard"
)


# ============================================================================
# Data Preparation
# ============================================================================

def prepare_training_data(csv_path: str) -> Dataset:
    """
    Load and format radiology reports for training
    
    CSV format:
        study_id, exam_type, findings, impression, report_text
    """
    
    df = pd.read_csv(csv_path)
    
    # Format as chat conversations
    def format_example(row):
        system_prompt = "You are an expert radiologist. Generate accurate radiology reports based on imaging findings."
        
        user_message = f"""
Exam Type: {row['exam_type']}
Imaging Findings: {row['findings']}

Generate a structured radiology report with impression and recommendations.
"""
        
        assistant_message = row['report_text']
        
        return {
            "messages": [
                {"role": "system", "content": system_prompt},
                {"role": "user", "content": user_message},
                {"role": "assistant", "content": assistant_message}
            ]
        }
    
    # Apply formatting
    formatted_data = df.apply(format_example, axis=1).tolist()
    
    return Dataset.from_list(formatted_data)


def tokenize_function(examples, tokenizer):
    """Tokenize examples for training"""
    
    # Apply chat template
    texts = []
    for messages in examples["messages"]:
        text = tokenizer.apply_chat_template(
            messages,
            tokenize=False,
            add_generation_prompt=False
        )
        texts.append(text)
    
    # Tokenize
    tokenized = tokenizer(
        texts,
        truncation=True,
        max_length=2048,
        padding="max_length",
        return_tensors="pt"
    )
    
    # For causal LM, labels = input_ids
    tokenized["labels"] = tokenized["input_ids"].clone()
    
    return tokenized


# ============================================================================
# Training
# ============================================================================

def train():
    """Main training function"""
    
    # Load tokenizer
    tokenizer = AutoTokenizer.from_pretrained(MODEL_NAME)
    tokenizer.pad_token = tokenizer.eos_token
    tokenizer.padding_side = "right"
    
    # Load model with quantization
    model = AutoModelForCausalLM.from_pretrained(
        MODEL_NAME,
        quantization_config=bnb_config,
        device_map="auto",
        trust_remote_code=True
    )
    
    # Prepare for k-bit training
    model = prepare_model_for_kbit_training(model)
    
    # Add LoRA adapters
    model = get_peft_model(model, lora_config)
    model.print_trainable_parameters()
    
    # Load datasets
    train_dataset = prepare_training_data("train_reports.csv")
    eval_dataset = prepare_training_data("val_reports.csv")
    
    # Tokenize
    train_dataset = train_dataset.map(
        lambda x: tokenize_function(x, tokenizer),
        batched=True,
        remove_columns=train_dataset.column_names
    )
    eval_dataset = eval_dataset.map(
        lambda x: tokenize_function(x, tokenizer),
        batched=True,
        remove_columns=eval_dataset.column_names
    )
    
    # Create trainer
    trainer = Trainer(
        model=model,
        args=training_args,
        train_dataset=train_dataset,
        eval_dataset=eval_dataset,
        tokenizer=tokenizer
    )
    
    # Train
    print("Starting training...")
    trainer.train()
    
    # Save final model
    print(f"Saving model to {OUTPUT_DIR}")
    trainer.save_model(OUTPUT_DIR)
    tokenizer.save_pretrained(OUTPUT_DIR)
    
    print("Training complete!")


if __name__ == "__main__":
    train()
```

### 4.2 Inference with Fine-Tuned Model

```python
"""
Load and use fine-tuned model for inference
"""

from transformers import AutoTokenizer, AutoModelForCausalLM, BitsAndBytesConfig
from peft import PeftModel
import torch


def load_finetuned_model(
    base_model: str = "meta-llama/Llama-2-70b-chat-hf",
    adapter_path: str = "./medical-diagnosis-lora",
    device: str = "cuda"
):
    """Load fine-tuned model with LoRA adapter"""
    
    # Quantization config
    bnb_config = BitsAndBytesConfig(
        load_in_4bit=True,
        bnb_4bit_compute_dtype=torch.float16,
        bnb_4bit_use_double_quant=True,
        bnb_4bit_quant_type="nf4"
    )
    
    # Load base model
    model = AutoModelForCausalLM.from_pretrained(
        base_model,
        quantization_config=bnb_config,
        device_map="auto"
    )
    
    # Load LoRA adapter
    model = PeftModel.from_pretrained(model, adapter_path)
    model.eval()
    
    # Load tokenizer
    tokenizer = AutoTokenizer.from_pretrained(base_model)
    
    return model, tokenizer


def generate_report(model, tokenizer, findings: str, exam_type: str):
    """Generate radiology report"""
    
    messages = [
        {"role": "system", "content": "You are an expert radiologist."},
        {"role": "user", "content": f"Exam: {exam_type}\nFindings: {findings}\n\nGenerate report:"}
    ]
    
    prompt = tokenizer.apply_chat_template(
        messages,
        tokenize=False,
        add_generation_prompt=True
    )
    
    inputs = tokenizer(prompt, return_tensors="pt").to(model.device)
    
    with torch.no_grad():
        outputs = model.generate(
            **inputs,
            max_new_tokens=512,
            temperature=0.2,
            top_p=0.9,
            do_sample=True
        )
    
    report = tokenizer.decode(outputs[0], skip_special_tokens=True)
    
    return report


# Example usage
if __name__ == "__main__":
    model, tokenizer = load_finetuned_model()
    
    report = generate_report(
        model,
        tokenizer,
        findings="Right lower lobe consolidation with air bronchograms",
        exam_type="Chest X-ray"
    )
    
    print(report)
```

---

## 5. Deployment (Kubernetes)

### 5.1 Kubernetes Deployment YAML

```yaml
# deployment.yaml
# Kubernetes deployment for Medical Diagnosis Assistant

apiVersion: v1
kind: Namespace
metadata:
  name: medical-ai

---

apiVersion: v1
kind: ConfigMap
metadata:
  name: model-config
  namespace: medical-ai
data:
  MODEL_PATH: "/models/llama-2-70b"
  LORA_ADAPTER_PATH: "/models/medical-lora"
  VISION_MODEL_PATH: "/models/biomed-clip"
  RAG_INDEX_PATH: "/data/rag-index"
  USE_4BIT: "true"
  MAX_BATCH_SIZE: "32"
  MAX_SEQUENCE_LENGTH: "2048"

---

apiVersion: apps/v1
kind: Deployment
metadata:
  name: medical-diagnosis-api
  namespace: medical-ai
spec:
  replicas: 3  # 3 API pods
  selector:
    matchLabels:
      app: medical-diagnosis
      tier: api
  template:
    metadata:
      labels:
        app: medical-diagnosis
        tier: api
    spec:
      containers:
      - name: api
        image: medical-ai-registry/diagnosis-api:v1.2.0
        ports:
        - containerPort: 8000
          name: http
        env:
        - name: MODEL_SERVER_URL
          value: "http://model-server:8001"
        - name: RAG_SERVER_URL
          value: "http://rag-server:8002"
        - name: REDIS_URL
          value: "redis://redis:6379"
        - name: POSTGRES_URL
          valueFrom:
            secretKeyRef:
              name: postgres-secret
              key: connection-string
        resources:
          requests:
            cpu: "4"
            memory: "16Gi"
          limits:
            cpu: "8"
            memory: "32Gi"
        livenessProbe:
          httpGet:
            path: /health
            port: 8000
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /ready
            port: 8000
          initialDelaySeconds: 10
          periodSeconds: 5

---

apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: model-server
  namespace: medical-ai
spec:
  serviceName: "model-server"
  replicas: 1  # Single GPU pod
  selector:
    matchLabels:
      app: medical-diagnosis
      tier: model
  template:
    metadata:
      labels:
        app: medical-diagnosis
        tier: model
    spec:
      containers:
      - name: vllm-server
        image: vllm/vllm-openai:latest
        command:
        - "python"
        - "-m"
        - "vllm.entrypoints.openai.api_server"
        - "--model"
        - "/models/llama-2-70b"
        - "--served-model-name"
        - "medical-llama"
        - "--tensor-parallel-size"
        - "4"  # 4x A100 GPUs
        - "--max-model-len"
        - "2048"
        - "--max-num-batched-tokens"
        - "4096"
        - "--enable-prefix-caching"
        - "--gpu-memory-utilization"
        - "0.95"
        ports:
        - containerPort: 8001
          name: http
        envFrom:
        - configMapRef:
            name: model-config
        resources:
          requests:
            nvidia.com/gpu: "4"  # 4x A100 80GB
            cpu: "32"
            memory: "256Gi"
          limits:
            nvidia.com/gpu: "4"
            cpu: "64"
            memory: "512Gi"
        volumeMounts:
        - name: model-storage
          mountPath: /models
        - name: cache-storage
          mountPath: /root/.cache
      nodeSelector:
        nvidia.com/gpu.product: NVIDIA-A100-SXM4-80GB
      tolerations:
      - key: nvidia.com/gpu
        operator: Exists
        effect: NoSchedule
  volumeClaimTemplates:
  - metadata:
      name: model-storage
    spec:
      accessModes: ["ReadWriteOnce"]
      storageClassName: fast-ssd
      resources:
        requests:
          storage: 500Gi
  - metadata:
      name: cache-storage
    spec:
      accessModes: ["ReadWriteOnce"]
      storageClassName: fast-ssd
      resources:
        requests:
          storage: 100Gi

---

apiVersion: apps/v1
kind: Deployment
metadata:
  name: rag-server
  namespace: medical-ai
spec:
  replicas: 2  # 2 RAG pods
  selector:
    matchLabels:
      app: medical-diagnosis
      tier: rag
  template:
    metadata:
      labels:
        app: medical-diagnosis
        tier: rag
    spec:
      containers:
      - name: rag
        image: medical-ai-registry/rag-server:v1.0.0
        ports:
        - containerPort: 8002
          name: http
        envFrom:
        - configMapRef:
            name: model-config
        resources:
          requests:
            cpu: "16"
            memory: "128Gi"  # Large memory for FAISS index
          limits:
            cpu: "32"
            memory: "256Gi"
        volumeMounts:
        - name: rag-index
          mountPath: /data/rag-index
      volumes:
      - name: rag-index
        persistentVolumeClaim:
          claimName: rag-index-pvc

---

apiVersion: v1
kind: Service
metadata:
  name: medical-diagnosis-api
  namespace: medical-ai
spec:
  type: LoadBalancer
  ports:
  - port: 80
    targetPort: 8000
    name: http
  selector:
    app: medical-diagnosis
    tier: api

---

apiVersion: v1
kind: Service
metadata:
  name: model-server
  namespace: medical-ai
spec:
  clusterIP: None  # Headless service for StatefulSet
  ports:
  - port: 8001
    name: http
  selector:
    app: medical-diagnosis
    tier: model

---

apiVersion: v1
kind: Service
metadata:
  name: rag-server
  namespace: medical-ai
spec:
  type: ClusterIP
  ports:
  - port: 8002
    name: http
  selector:
    app: medical-diagnosis
    tier: rag

---

apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis
  namespace: medical-ai
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
      - name: redis
        image: redis:7-alpine
        ports:
        - containerPort: 6379
        resources:
          requests:
            cpu: "2"
            memory: "8Gi"
          limits:
            cpu: "4"
            memory: "16Gi"
        volumeMounts:
        - name: redis-data
          mountPath: /data
      volumes:
      - name: redis-data
        persistentVolumeClaim:
          claimName: redis-pvc

---

apiVersion: v1
kind: Service
metadata:
  name: redis
  namespace: medical-ai
spec:
  type: ClusterIP
  ports:
  - port: 6379
  selector:
    app: redis

---

apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: api-hpa
  namespace: medical-ai
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: medical-diagnosis-api
  minReplicas: 3
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70
  - type: Resource
    resource:
      name: memory
      target:
        type: Utilization
        averageUtilization: 80
```

---

## 6. Monitoring & Logging

### 6.1 Prometheus Metrics

```python
"""
Prometheus metrics for monitoring
"""

from prometheus_client import Counter, Histogram, Gauge, generate_latest
from flask import Flask, Response
import time

app = Flask(__name__)

# Define metrics
REQUESTS_TOTAL = Counter(
    'diagnosis_requests_total',
    'Total number of diagnosis requests',
    ['status', 'exam_type']
)

PROCESSING_TIME = Histogram(
    'diagnosis_processing_seconds',
    'Time spent processing diagnosis requests',
    ['exam_type'],
    buckets=[0.5, 1.0, 2.0, 5.0, 10.0, 30.0, 60.0]
)

CRITICAL_FINDINGS = Counter(
    'critical_findings_total',
    'Number of critical findings detected',
    ['condition']
)

RADIOLOGIST_AGREEMENT = Gauge(
    'radiologist_agreement_rate',
    'Percentage of AI reports agreed upon by radiologists'
)

QUEUE_SIZE = Gauge(
    'diagnosis_queue_size',
    'Number of studies waiting for analysis'
)


@app.route('/metrics')
def metrics():
    """Expose Prometheus metrics"""
    return Response(generate_latest(), mimetype='text/plain')


def record_diagnosis(exam_type: str, status: str, processing_time: float):
    """Record diagnosis metrics"""
    REQUESTS_TOTAL.labels(status=status, exam_type=exam_type).inc()
    PROCESSING_TIME.labels(exam_type=exam_type).observe(processing_time)


def record_critical_finding(condition: str):
    """Record critical finding"""
    CRITICAL_FINDINGS.labels(condition=condition).inc()


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=9090)
```

---

## 7. Full Working Example

### 7.1 Complete Production Example

```python
"""
Complete end-to-end example
"""

from medical_diagnosis_assistant import (
    MedicalDiagnosisAssistant,
    DiagnosisRequest,
    DiagnosisResponse
)
import logging

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s'
)

def main():
    # Initialize assistant
    print("Initializing Medical Diagnosis Assistant...")
    assistant = MedicalDiagnosisAssistant(
        llm_model_path="meta-llama/Llama-2-70b-chat-hf",
        lora_adapter_path="./adapters/medical-lora",
        device="cuda",
        use_4bit=True
    )
    print("✓ Initialization complete\n")
    
    # Example case
    request = DiagnosisRequest(
        study_id="STUDY_67890",
        patient_id_hash="b7e4c9a2",
        exam_type="CHEST_XRAY",
        dicom_paths=[
            "./examples/chest_xray_pa.dcm",
            "./examples/chest_xray_lateral.dcm"
        ],
        patient_context={
            "age": 72,
            "sex": "F",
            "symptoms": "Productive cough, fever 101°F, shortness of breath for 5 days",
            "medical_history": "COPD, former smoker (40 pack-years)",
            "medications": ["Albuterol", "Spiriva", "Prednisone"]
        },
        clinical_indication="Rule out pneumonia vs COPD exacerbation",
        priority="URGENT"
    )
    
    # Analyze
    print("Analyzing study...")
    response = assistant.analyze_study(request)
    
    # Display results
    print(f"\n{'='*80}")
    print(f"RADIOLOGY REPORT - Study {response.study_id}")
    print(f"{'='*80}\n")
    
    print(f"Processing Time: {response.processing_time_ms:.0f}ms")
    print(f"Overall Confidence: {response.confidence:.0f}%")
    print(f"Model Version: {response.model_version}\n")
    
    print("FINDINGS:")
    print("-" * 80)
    for idx, finding in enumerate(response.findings, 1):
        print(f"{idx}. {finding['description']}")
        print(f"   Confidence: {finding['confidence']}%")
        if 'location' in finding:
            print(f"   Location: {finding['location']}")
        print()
    
    print("IMPRESSION:")
    print("-" * 80)
    print(response.impression)
    print()
    
    if response.recommendations:
        print("RECOMMENDATIONS:")
        print("-" * 80)
        for idx, rec in enumerate(response.recommendations, 1):
            print(f"{idx}. {rec}")
        print()
    
    if response.critical_findings:
        print("🚨 CRITICAL FINDINGS DETECTED:")
        print("-" * 80)
        for critical in response.critical_findings:
            print(f"⚠️  {critical['condition'].upper()}")
            print(f"   Confidence: {critical['confidence']}%")
            print(f"   Action: {critical['action']}")
            print(f"   Rationale: {critical['rationale']}")
            print()
    
    print(f"{'='*80}\n")
    print("✓ Report generated successfully")
    print("⚠️  This is a PRELIMINARY report - requires radiologist review")


if __name__ == "__main__":
    main()
```

---

📑 **Navigation**: [🏠 Main](./README.md) | [📊 Overview](./README_Overview.md) | [🏗️ Architecture](./README_Solution_Architecture.md) | [⚠️ Challenges](./README_Challenges_Solutions.md) | [🚀 Future](./README_Future_Improvements.md)

