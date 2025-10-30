# ☁️ Deployment & Ops

Model serving, optimization, scaling, monitoring.

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
- **URL:** https://github.com/triton-inference-server/server
- **Type:** Inference Server
- **Maintainer:** NVIDIA
- **License:** BSD 3-Clause
- **Note:** Multi-framework inference serving.
