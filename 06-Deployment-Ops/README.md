# ☁️ Deployment & Ops

Model serving, optimization, scaling, monitoring.

## 📊 Legend

- 🟢 **Easy** - Quick setup, beginner-friendly
- 🟡 **Moderate** - Some DevOps experience needed  
- 🔴 **Complex** - Advanced setup, production-grade
- ⚡ **Performance** - Speed/throughput rating
- 💰 **Cost** - Resource requirements
- 📅 **Updated** - Last verified
- 🏢 **Production-Ready** - Battle-tested at scale

---

## 🚀 Inference Servers

### vLLM
- **URL:** https://github.com/vllm-project/vllm
- **Type:** Inference Engine
- **License:** Apache 2.0
- **Note:** High-throughput serving with PagedAttention, continuous batching.

### Text Generation Inference (TGI)
- **URL:** https://github.com/huggingface/text-generation-inference
- **Type:** Inference Server
- **Maintainer:** Hugging Face
- **License:** Apache 2.0
- **Note:** Production LLM serving with tensor parallelism, streaming.

### llama.cpp
- **URL:** https://github.com/ggerganov/llama.cpp
- **Type:** Inference Engine
- **License:** MIT
- **Note:** Pure C/C++ implementation for CPU/Metal/CUDA inference.

### Ollama
- **URL:** https://github.com/ollama/ollama
- **Type:** Local LLM Server
- **License:** MIT
- **Note:** Simple API for running LLMs locally.

### LocalAI
- **URL:** https://github.com/mudler/LocalAI
- **Type:** Inference Server
- **License:** MIT
- **Note:** OpenAI-compatible API for local models.

### FastChat
- **URL:** https://github.com/lm-sys/FastChat
- **Type:** Serving Platform
- **License:** Apache 2.0
- **Note:** Training, serving, and evaluation for chatbots.

### Ray Serve
- **URL:** https://docs.ray.io/en/latest/serve/index.html
- **Type:** Serving Framework
- **License:** Apache 2.0
- **Note:** Scalable model serving with Ray.

---

## ⚙️ Optimization Techniques

### FlashAttention
- **URL:** https://github.com/Dao-AILab/flash-attention
- **Type:** Attention Implementation
- **License:** BSD 3-Clause
- **Note:** Fast and memory-efficient attention (2-4x speedup).

### FlashAttention-2
- **URL:** https://arxiv.org/abs/2307.08691
- **Type:** Paper + Implementation
- **Year:** 2023
- **Note:** Further optimized attention mechanism.

### PagedAttention (vLLM)
- **URL:** https://arxiv.org/abs/2309.06180
- **Title:** Efficient Memory Management for Large Language Model Serving
- **Year:** 2023
- **Note:** Memory-efficient attention for serving.

### Continuous Batching
- **URL:** https://www.anyscale.com/blog/continuous-batching-llm-inference
- **Type:** Blog Post
- **Note:** Dynamic batching technique for higher throughput.

---

## 🗜️ Quantization

### bitsandbytes
- **URL:** https://github.com/TimDettmers/bitsandbytes
- **Type:** Library
- **License:** MIT
- **Note:** 8-bit and 4-bit quantization for PyTorch.

### GPTQ: Accurate Post-Training Quantization
- **URL:** https://arxiv.org/abs/2210.17323
- **Type:** Paper
- **Year:** 2022
- **Note:** Post-training quantization method.

### AutoGPTQ
- **URL:** https://github.com/PanQiWei/AutoGPTQ
- **Type:** Library
- **License:** MIT
- **Note:** Easy-to-use GPTQ implementation.

### AWQ: Activation-aware Weight Quantization
- **URL:** https://github.com/mit-han-lab/llm-awq
- **Type:** Library
- **License:** MIT
- **Note:** Efficient 4-bit quantization preserving accuracy.

### SmoothQuant
- **URL:** https://github.com/mit-han-lab/smoothquant
- **Type:** Library
- **License:** MIT
- **Note:** Quantization for both weights and activations.

### GGML / GGUF Format
- **URL:** https://github.com/ggerganov/ggml
- **Type:** Library + Format
- **License:** MIT
- **Note:** Quantized model format for llama.cpp.

---

## 🔧 Model Compression

### Pruning
- **URL:** https://arxiv.org/abs/2301.00774
- **Title:** The Lottery Ticket Hypothesis for LLMs
- **Year:** 2023
- **Note:** Sparse subnetworks in language models.

### Knowledge Distillation
- **URL:** https://arxiv.org/abs/1503.02531
- **Title:** Distilling the Knowledge in a Neural Network
- **Authors:** Hinton et al.
- **Year:** 2015
- **Note:** Original distillation paper.

### DistilBERT
- **URL:** https://arxiv.org/abs/1910.01108
- **Title:** DistilBERT, a distilled version of BERT
- **Year:** 2019
- **Note:** 40% smaller, 60% faster BERT variant.

---

## ☁️ Cloud Deployment

### Hugging Face Inference Endpoints
- **URL:** https://huggingface.co/inference-endpoints
- **Type:** Managed Service
- **Note:** Deploy models with autoscaling (pay-per-use).

### AWS SageMaker
- **URL:** https://aws.amazon.com/sagemaker/
- **Type:** Cloud Platform
- **Note:** Managed ML deployment (free tier available).

### Google Cloud Vertex AI
- **URL:** https://cloud.google.com/vertex-ai
- **Type:** Cloud Platform
- **Note:** Managed ML platform (free tier available).

### Azure Machine Learning
- **URL:** https://azure.microsoft.com/en-us/services/machine-learning/
- **Type:** Cloud Platform
- **Note:** Managed ML deployment (free tier available).

### Replicate
- **URL:** https://replicate.com/
- **Type:** Model Hosting
- **Note:** Run models in the cloud (pay-per-use).

### Modal
- **URL:** https://modal.com/
- **Type:** Serverless Platform
- **Note:** Run LLMs serverlessly (free tier available).

### Banana.dev
- **URL:** https://www.banana.dev/
- **Type:** Serverless Inference
- **Note:** GPU serverless platform for ML models.

---

## 🐳 Containerization

### Docker
- **URL:** https://www.docker.com/
- **Type:** Containerization Platform
- **License:** Apache 2.0 (Engine)
- **Note:** Standard container runtime.

### NVIDIA Container Toolkit
- **URL:** https://github.com/NVIDIA/nvidia-docker
- **Type:** Container Tool
- **License:** Apache 2.0
- **Note:** GPU support for Docker containers.

### TorchServe
- **URL:** https://github.com/pytorch/serve
- **Type:** Model Server
- **License:** Apache 2.0
- **Note:** PyTorch model serving framework.

---

## 📊 Monitoring & Observability

### Prometheus
- **URL:** https://prometheus.io/
- **Type:** Monitoring System
- **License:** Apache 2.0
- **Note:** Metrics collection and alerting.

### Grafana
- **URL:** https://grafana.com/
- **Type:** Visualization Platform
- **License:** AGPL 3.0 (open-source version)
- **Note:** Metrics dashboards and visualization.

### LangSmith
- **URL:** https://smith.langchain.com/
- **Type:** LLM Monitoring
- **Maintainer:** LangChain
- **Note:** Debugging and monitoring LLM applications (free tier).

### Weights & Biases
- **URL:** https://wandb.ai/
- **Type:** ML Platform
- **Note:** Experiment tracking and monitoring (free for open-source).

### Phoenix (Arize AI)
- **URL:** https://github.com/Arize-ai/phoenix
- **Type:** Observability Tool
- **License:** Elastic License 2.0
- **Note:** Open-source LLM observability.

---

## 🔒 Security

### NeMo Guardrails
- **URL:** https://github.com/NVIDIA/NeMo-Guardrails
- **Type:** Framework
- **Maintainer:** NVIDIA
- **License:** Apache 2.0
- **Note:** Safety guardrails for LLM applications.

### Garak: LLM Vulnerability Scanner
- **URL:** https://github.com/leondz/garak
- **Type:** Security Tool
- **License:** Apache 2.0
- **Note:** Vulnerability scanner for LLMs.

### PromptInject
- **URL:** https://github.com/agencyenterprise/PromptInject
- **Type:** Research + Tool
- **License:** MIT
- **Note:** Prompt injection detection framework.

---

## 🚦 Load Balancing & Routing

### LiteLLM Proxy
- **URL:** https://github.com/BerriAI/litellm
- **Type:** Proxy Server
- **License:** MIT
- **Note:** Load balance across 100+ LLM providers.

### OpenLLM
- **URL:** https://github.com/bentoml/OpenLLM
- **Type:** Deployment Framework
- **License:** Apache 2.0
- **Note:** Deploy, serve, and monitor LLMs.

---

## 📚 Learning Resources

### Deploying LLMs in Production
- **URL:** https://huyenchip.com/2023/04/11/llm-engineering.html
- **Type:** Blog Post
- **Author:** Chip Huyen
- **Note:** Comprehensive guide to LLM deployment challenges.

### LLM Inference Optimization
- **URL:** https://lilianweng.github.io/posts/2023-01-10-inference-optimization/
- **Type:** Blog Post
- **Author:** Lilian Weng
- **Note:** Overview of inference optimization techniques.

### Full Stack LLM Bootcamp
- **URL:** https://fullstackdeeplearning.com/llm-bootcamp/
- **Type:** Course Materials
- **Note:** Deployment and production best practices.

---

## 🧪 Benchmarking Tools

### llama-bench
- **URL:** https://github.com/ggerganov/llama.cpp/tree/master/examples/llama-bench
- **Type:** Benchmarking Tool
- **Note:** Benchmark llama.cpp performance.

### vllm-benchmark
- **URL:** https://github.com/vllm-project/vllm/tree/main/benchmarks
- **Type:** Benchmarking Tool
- **Note:** Throughput and latency benchmarks.

---

## ⚡ Acceleration

### TensorRT-LLM
- **URL:** https://github.com/NVIDIA/TensorRT-LLM
- **Type:** Inference SDK
- **Maintainer:** NVIDIA
- **License:** Apache 2.0
- **Note:** Optimized LLM inference on NVIDIA GPUs.

### DeepSpeed-MII
- **URL:** https://github.com/microsoft/DeepSpeed-MII
- **Type:** Inference System
- **Maintainer:** Microsoft
- **License:** Apache 2.0
- **Note:** Low-latency, low-cost inference.

### Triton Inference Server
- 🔴 Complex | ⚡⚡⚡⚡⚡ Excellent | 📅 Oct 2025 | 🏢 Production
- **URL:** https://github.com/triton-inference-server/server
- **Type:** Inference Server
- **Maintainer:** NVIDIA
- **License:** BSD 3-Clause
- **Note:** Multi-framework inference serving.

---

## 🔀 Deployment Comparison Tables

### Inference Servers Performance

| Server | Throughput | Latency | Hardware | Setup Complexity | Best For |
|--------|------------|---------|----------|------------------|----------|
| **vLLM** | ⚡⚡⚡⚡⚡ Best | ⚡⚡⚡⚡ Low | GPU | 🟢 Easy | High-throughput production |
| **TGI** | ⚡⚡⚡⚡ High | ⚡⚡⚡⚡ Low | GPU | 🟢 Easy | HF models, streaming |
| **llama.cpp** | ⚡⚡⚡ Good | ⚡⚡⚡ Medium | CPU/GPU/Metal | 🟢 Easy | Local, CPU inference |
| **Ollama** | ⚡⚡⚡ Good | ⚡⚡⚡ Medium | CPU/GPU | 🟢 Very Easy | Development, local API |
| **TensorRT-LLM** | ⚡⚡⚡⚡⚡ Best | ⚡⚡⚡⚡⚡ Lowest | NVIDIA GPU | 🔴 Complex | Maximum performance |
| **LocalAI** | ⚡⚡ Moderate | ⚡⚡⚡ Medium | CPU/GPU | 🟢 Easy | OpenAI-compatible local |

### Quantization Methods

| Method | Model Size | Speed | Accuracy | Use Case |
|--------|------------|-------|----------|----------|
| **FP16** | 50% | ⚡⚡⚡⚡ Fast | ⭐⭐⭐⭐⭐ Perfect | GPU with FP16 support |
| **INT8** | 25% | ⚡⚡⚡⚡⚡ Very Fast | ⭐⭐⭐⭐ Very Good | Production, minimal loss |
| **INT4** | 12.5% | ⚡⚡⚡⚡⚡ Very Fast | ⭐⭐⭐ Good | Consumer GPUs |
| **GPTQ** | 12.5-25% | ⚡⚡⚡⚡⚡ Very Fast | ⭐⭐⭐⭐ Very Good | Optimal quality/size |
| **AWQ** | 12.5-25% | ⚡⚡⚡⚡⚡ Very Fast | ⭐⭐⭐⭐ Very Good | Activation-aware |
| **GGUF** | Variable | ⚡⚡⚡⚡ Fast | ⭐⭐⭐ Good | llama.cpp, CPU |

### Cloud Platform Comparison

| Platform | Ease of Use | Cost | GPU Options | Spot/Preemptible | Best For |
|----------|-------------|------|-------------|------------------|----------|
| **HF Inference** | 🟢 Very Easy | 💰💰 Low | Limited | ❌ No | Quick deployment, testing |
| **AWS SageMaker** | 🟡 Moderate | 💰💰💰 High | Excellent | ✅ Yes | Enterprise, flexible |
| **GCP Vertex AI** | 🟡 Moderate | 💰💰💰 High | Good | ✅ Yes | Google ecosystem |
| **Azure ML** | 🟡 Moderate | 💰💰💰 High | Good | ✅ Yes | Microsoft stack |
| **RunPod** | 🟢 Easy | 💰💰 Low | Excellent | ✅ Yes | Cost-effective GPUs |
| **Lambda Labs** | 🟢 Easy | 💰💰 Low | Good | ❌ No | Budget-friendly |
| **Modal** | 🟢 Easy | 💰💰 Medium | Good | ❌ Auto-scale | Serverless deployment |

### Optimization Techniques Impact

| Technique | Throughput Gain | Memory Saving | Implementation | Accuracy Impact |
|-----------|-----------------|---------------|----------------|-----------------|
| **PagedAttention** | 2-3x | 50%+ | vLLM | None |
| **Continuous Batching** | 2-10x | Minimal | vLLM, TGI | None |
| **FlashAttention-2** | 2x | 30% | PyTorch, vLLM | None |
| **Tensor Parallelism** | Linear | None | TGI, vLLM | None |
| **INT8 Quantization** | 1.5-2x | 50% | AutoGPTQ, bitsandbytes | Minimal |
| **Speculative Decoding** | 2-3x | None | Complex setup | None |

---

## 🎓 Deployment Strategy Guide

### Phase 1: Development (Local)
**Tools**: Ollama, llama.cpp, LM Studio
- 🎯 **Goal**: Fast iteration, testing
- 💰 **Cost**: Free (your hardware)
- 📊 **Scale**: Single user
- ⏱️ **Setup**: 5-10 minutes

### Phase 2: MVP/Beta (Small Scale)
**Tools**: HF Inference Endpoints, Modal, RunPod
- 🎯 **Goal**: 10-1000 users
- 💰 **Cost**: $50-500/month
- 📊 **Scale**: Light production
- ⏱️ **Setup**: 1-2 hours

### Phase 3: Production (Medium Scale)
**Tools**: vLLM + K8s, TGI + Docker, Cloud managed
- 🎯 **Goal**: 1K-100K users
- 💰 **Cost**: $500-5K/month
- 📊 **Scale**: Real production
- ⏱️ **Setup**: 1-2 days

### Phase 4: Enterprise (Large Scale)
**Tools**: TensorRT-LLM, Custom infra, Multi-region
- 🎯 **Goal**: 100K+ users
- 💰 **Cost**: $5K+/month
- 📊 **Scale**: High availability
- ⏱️ **Setup**: 1-2 weeks

---

## 🔑 Key Decision Points

**Choose vLLM if:**
- Need maximum throughput
- Serving many concurrent users
- Using standard model architectures
- Have GPU infrastructure

**Choose TGI if:**
- Using Hugging Face models
- Need streaming responses
- Want built-in safety features
- Prefer official HF support

**Choose llama.cpp if:**
- Running on CPU or Apple Silicon
- Edge/mobile deployment
- Memory constrained
- Need offline inference

**Choose Ollama if:**
- Local development
- Simple API needed
- Quick prototyping
- Non-production use

**Choose TensorRT-LLM if:**
- Need absolute best performance
- Have NVIDIA GPUs
- Can handle complex setup
- Production scale deployment

---

## 💡 Cost Optimization Tips

1. **Use quantization**: INT8 reduces cost by 50% with minimal quality loss
2. **Spot instances**: Save 60-80% on cloud costs (use for batch processing)
3. **Continuous batching**: Maximize GPU utilization (vLLM, TGI)
4. **Right-size models**: 7B models often sufficient (not always need 70B)
5. **Cache common queries**: Reduce redundant inference
6. **Use smaller context**: Reduce memory and latency
7. **Auto-scaling**: Scale down during low traffic
8. **Regional deployment**: Use cheapest regions for development

---

## 📊 Monitoring Essentials

**Must-Track Metrics:**
- ⏱️ **Latency**: P50, P95, P99 response times
- 📊 **Throughput**: Requests per second
- 💾 **GPU Memory**: Utilization percentage
- 🔥 **GPU Utilization**: Compute usage
- ❌ **Error Rate**: Failed requests percentage
- 💰 **Cost per Request**: Operational costs

**Tools Stack:**
- Prometheus + Grafana (metrics)
- LangSmith (LLM-specific tracing)
- Weights & Biases (experiment tracking)
- OpenTelemetry (distributed tracing)

---

**Last Updated:** October 2025
