# 🛠️ Tools and Libraries for LLM Engineering

A comprehensive collection of free, open-source frameworks, libraries, and platforms for working with Large Language Models.

---

## 🎯 Categories

- [Model Libraries](#-model-libraries)
- [Training Frameworks](#-training-frameworks)
- [Inference Engines](#-inference-engines)
- [Application Frameworks](#-application-frameworks)
- [Vector Databases](#-vector-databases)
- [Evaluation Tools](#-evaluation-tools)
- [Deployment Platforms](#-deployment-platforms)
- [Development Tools](#-development-tools)

---

## 📚 Model Libraries

### 🌟 **Hugging Face Transformers**
**Link**: https://github.com/huggingface/transformers  
**License**: Apache 2.0  
**⭐ Stars**: 120K+

**Features**:
- 100K+ pre-trained models
- Easy-to-use API
- PyTorch & TensorFlow support
- Extensive documentation

**Why Use**: Industry standard, largest model hub

**Quick Start**:
```python
from transformers import pipeline
pipe = pipeline("text-generation", model="gpt2")
```

---

### **PEFT (Parameter-Efficient Fine-Tuning)**
**Link**: https://github.com/huggingface/peft  
**License**: Apache 2.0

**Methods**:
- LoRA
- QLoRA
- Prefix Tuning
- P-Tuning
- Adapter layers

**Why Use**: Fine-tune large models efficiently

---

### **Sentence Transformers**
**Link**: https://www.sbert.net/  
**License**: Apache 2.0

**Purpose**: Sentence embeddings

**Models**: 100+ optimized models

**Use Cases**: Semantic search, clustering, similarity

---

## 🚀 Training Frameworks

### 🌟 **DeepSpeed** (Microsoft)
**Link**: https://www.deepspeed.ai/  
**License**: MIT  
**⭐ Stars**: 30K+

**Features**:
- ZeRO optimizer
- 3D parallelism
- 1-click RLHF
- Mixture of Experts

**Why Use**: Train trillion-parameter models

---

### **Megatron-LM** (NVIDIA)
**Link**: https://github.com/NVIDIA/Megatron-LM  
**License**: Custom

**Features**:
- Model parallelism
- Pipeline parallelism
- Efficient GPU utilization
- Production-proven

---

### **PyTorch Lightning**
**Link**: https://www.lightning.ai/  
**License**: Apache 2.0

**Features**:
- Simplified training loops
- Automatic distributed training
- Easy callbacks
- Great for research

---

### **Accelerate** (Hugging Face)
**Link**: https://github.com/huggingface/accelerate  
**License**: Apache 2.0

**Features**:
- Same code, any setup
- Easy distributed training
- Mixed precision
- DeepSpeed/FSDP integration

---

## ⚡ Inference Engines

### 🌟 **vLLM**
**Link**: https://github.com/vllm-project/vllm  
**License**: Apache 2.0  
**⭐ Stars**: 15K+

**Features**:
- PagedAttention
- 24x faster than HF
- Continuous batching
- Optimized for throughput

**Why Use**: Production inference, highest throughput

---

### **Text Generation Inference** (Hugging Face)
**Link**: https://github.com/huggingface/text-generation-inference  
**License**: Apache 2.0

**Features**:
- Production-ready
- Quantization support
- Streaming
- Flash Attention

---

### **llama.cpp**
**Link**: https://github.com/ggerganov/llama.cpp  
**License**: MIT  
**⭐ Stars**: 50K+

**Features**:
- C++ implementation
- CPU inference
- Quantization (2-8 bit)
- Mac Metal support

**Why Use**: Run LLMs on CPU/Mac

---

### **Ollama**
**Link**: https://ollama.ai/  
**License**: MIT

**Features**:
- Easy local deployment
- One-command model download
- API compatible with OpenAI
- Cross-platform

**Why Use**: Simplest way to run LLMs locally

---

### **CTranslate2**
**Link**: https://github.com/OpenNMT/CTranslate2  
**License**: MIT

**Features**:
- 4x faster inference
- Quantization support
- Multiple backends
- Low memory usage

---

## 🔧 Application Frameworks

### 🌟 **LangChain**
**Link**: https://www.langchain.com/  
**License**: MIT  
**⭐ Stars**: 80K+

**Features**:
- Chains & agents
- RAG support
- Memory management
- Tool integration
- 100+ integrations

**Why Use**: Build complex LLM applications

**Components**:
- Models: LLM wrappers
- Prompts: Template management
- Chains: Sequence workflows
- Agents: Autonomous systems
- Memory: Context management

---

### **LlamaIndex**
**Link**: https://www.llamaindex.ai/  
**License**: MIT  
**⭐ Stars**: 30K+

**Features**:
- Data connectors (100+)
- Index structures
- Query engines
- RAG optimization
- Agent frameworks

**Why Use**: Best for RAG & data-centric apps

---

### **Haystack** (deepset)
**Link**: https://haystack.deepset.ai/  
**License**: Apache 2.0

**Features**:
- NLP pipelines
- Question answering
- Document search
- Production-ready

---

### **Semantic Kernel** (Microsoft)
**Link**: https://github.com/microsoft/semantic-kernel  
**License**: MIT

**Features**:
- AI orchestration
- Skills & planning
- Memory connectors
- Multi-language (C#, Python, Java)

**Why Use**: Enterprise applications

---

## 🗄️ Vector Databases

### **ChromaDB**
**Link**: https://www.trychroma.com/  
**License**: Apache 2.0

**Features**:
- Embedded database
- Python/JS client
- Easy to use
- Free & open-source

**Why Use**: Simplest vector DB for prototyping

---

### **FAISS** (Facebook)
**Link**: https://github.com/facebookresearch/faiss  
**License**: MIT

**Features**:
- Billion-scale similarity search
- GPU acceleration
- Multiple index types
- Highly optimized

**Why Use**: High-performance search

---

### **Weaviate**
**Link**: https://weaviate.io/  
**License**: BSD 3-Clause

**Features**:
- GraphQL API
- Hybrid search
- Module system
- Cloud available (free tier)

---

### **Milvus**
**Link**: https://milvus.io/  
**License**: Apache 2.0

**Features**:
- Cloud-native
- Highly scalable
- Multiple index types
- Production-ready

---

### **Qdrant**
**Link**: https://qdrant.tech/  
**License**: Apache 2.0

**Features**:
- Rust-based (fast)
- Payload filtering
- Distributed
- Cloud available

---

## 📊 Evaluation Tools

### **lm-evaluation-harness** (EleutherAI)
**Link**: https://github.com/EleutherAI/lm-evaluation-harness  
**License**: MIT

**Features**:
- 200+ tasks
- Standardized evaluation
- Easy to extend
- Reproducible

---

### **Hugging Face Evaluate**
**Link**: https://huggingface.co/docs/evaluate/  
**License**: Apache 2.0

**Features**:
- 100+ metrics
- Easy integration
- Distributed evaluation
- Custom metrics

---

### **HELM** (Stanford)
**Link**: https://github.com/stanford-crfm/helm  
**License**: Apache 2.0

**Features**:
- Holistic evaluation
- 42 scenarios
- Transparency
- Standardized

---

## ☁️ Deployment Platforms

### **Hugging Face Spaces**
**Link**: https://huggingface.co/spaces  
**Free Tier**: Yes

**Features**:
- Gradio/Streamlit apps
- Free GPU (limited)
- Easy deployment
- Community

---

### **Google Colab**
**Link**: https://colab.research.google.com/  
**Free Tier**: Yes

**Features**:
- Free GPU/TPU
- Jupyter notebooks
- Google Drive integration
- Pre-installed libraries

---

### **Kaggle Notebooks**
**Link**: https://www.kaggle.com/code  
**Free Tier**: Yes

**Features**:
- Free GPU (30h/week)
- TPU support
- Dataset integration
- Sharing & collaboration

---

### **Replicate**
**Link**: https://replicate.com/  
**Free Tier**: Limited

**Features**:
- One-line deployment
- Serverless
- Pay-per-use
- API access

---

## 🔬 Development Tools

### **Tokenizers** (Hugging Face)
**Link**: https://github.com/huggingface/tokenizers  
**License**: Apache 2.0

**Features**:
- Fast tokenization (Rust)
- BPE, WordPiece, Unigram
- Training custom tokenizers

---

### **Weights & Biases**
**Link**: https://wandb.ai/  
**Free Tier**: Yes

**Features**:
- Experiment tracking
- Hyperparameter tuning
- Model versioning
- Free for academics

---

### **TensorBoard**
**Link**: https://www.tensorflow.org/tensorboard  
**License**: Apache 2.0

**Features**:
- Visualization
- Metric tracking
- Model graphs
- Free & open-source

---

### **Jupyter Notebooks**
**Link**: https://jupyter.org/  
**License**: BSD

**Features**:
- Interactive development
- Mixed code/text
- Visualization
- Extension ecosystem

---

## 🎨 Prompt Engineering Tools

### **OpenAI Playground**
**Link**: https://platform.openai.com/playground  
**Free Tier**: Limited

**Features**:
- Interactive testing
- Parameter tuning
- Prompt templates

---

### **LangSmith** (LangChain)
**Link**: https://www.langchain.com/langsmith  
**Free Tier**: Yes

**Features**:
- Prompt management
- Testing & debugging
- Monitoring
- Evaluation

---

### **PromptFlow** (Microsoft)
**Link**: https://microsoft.github.io/promptflow/  
**License**: MIT

**Features**:
- Visual prompt engineering
- Testing & evaluation
- CI/CD integration

---

## 🧪 Specialized Tools

### **AutoGPT**
**Link**: https://github.com/Significant-Gravitas/AutoGPT  
**License**: MIT

**Purpose**: Autonomous AI agents

---

### **GPT-Engineer**
**Link**: https://github.com/gpt-engineer-org/gpt-engineer  
**License**: MIT

**Purpose**: Code generation from prompts

---

### **Guidance** (Microsoft)
**Link**: https://github.com/guidance-ai/guidance  
**License**: MIT

**Purpose**: Controlled generation

---

### **Outlines**
**Link**: https://github.com/outlines-dev/outlines  
**License**: Apache 2.0

**Purpose**: Structured text generation

---

## 📱 APIs & SDKs

### **OpenAI Python**
**Link**: https://github.com/openai/openai-python  
**License**: MIT

**Features**: Official OpenAI client

---

### **Anthropic Python**
**Link**: https://github.com/anthropics/anthropic-sdk-python  
**License**: MIT

**Features**: Official Claude client

---

### **Google Generative AI**
**Link**: https://github.com/google/generative-ai-python  
**License**: Apache 2.0

**Features**: Gemini API client

---

## 🎯 Tool Selection Guide

### For Learning & Experimentation
✅ Hugging Face Transformers  
✅ Google Colab  
✅ Ollama (local)  
✅ ChromaDB  

### For Research
✅ PyTorch Lightning  
✅ Weights & Biases  
✅ lm-evaluation-harness  
✅ Hugging Face Datasets  

### For Production
✅ vLLM  
✅ Text Generation Inference  
✅ LangChain/LlamaIndex  
✅ Weaviate/Milvus  
✅ DeepSpeed  

### For Fine-Tuning
✅ PEFT  
✅ Accelerate  
✅ DeepSpeed  
✅ TRL (Transformer RL)  

---

## 💡 Getting Started Recommendations

### Week 1: Basics
- Install Hugging Face Transformers
- Try models in Colab
- Experiment with Ollama locally

### Week 2: Applications
- Build with LangChain
- Set up ChromaDB
- Create a simple RAG app

### Week 3: Advanced
- Try vLLM for inference
- Experiment with PEFT
- Track experiments with W&B

---

## 🔗 Resource Hubs

**Hugging Face**: https://huggingface.co/  
- Models, datasets, spaces, docs

**GitHub**: https://github.com/  
- Search "awesome-llm" for curated lists

**Papers with Code**: https://paperswithcode.com/  
- Papers + implementations

---

<div align="center">

**[⬆ Back to Top](#-tools-and-libraries-for-llm-engineering)**

*"The right tools make all the difference."*

</div>
