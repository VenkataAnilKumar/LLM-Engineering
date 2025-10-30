# 🛠️ Frameworks

Libraries and frameworks for LLM development: Hugging Face, LangChain, Ollama, LlamaIndex, etc.

---

## 🤗 Hugging Face Ecosystem

### Transformers
- **URL:** https://github.com/huggingface/transformers
- **Type:** Library
- **License:** Apache 2.0
- **Note:** 500K+ models, PyTorch/TensorFlow/JAX support.

### PEFT: Parameter-Efficient Fine-Tuning
- **URL:** https://github.com/huggingface/peft
- **Type:** Library
- **License:** Apache 2.0
- **Note:** LoRA, QLoRA, Prefix Tuning, P-Tuning implementations.

### TRL: Transformer Reinforcement Learning
- **URL:** https://github.com/huggingface/trl
- **Type:** Library
- **License:** Apache 2.0
- **Note:** PPO, DPO, RLHF training methods.

### Accelerate
- **URL:** https://github.com/huggingface/accelerate
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Simplified distributed training wrapper.

### Tokenizers
- **URL:** https://github.com/huggingface/tokenizers
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Fast BPE, WordPiece, Unigram tokenizers.

### Datasets
- **URL:** https://github.com/huggingface/datasets
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Loading and processing datasets with memory mapping.

### Optimum
- **URL:** https://github.com/huggingface/optimum
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Hardware optimization (ONNX, OpenVINO, TensorRT).

---

## 🦙 LLM Deployment Frameworks

### Ollama
- **URL:** https://github.com/ollama/ollama
- **Type:** Local LLM Server
- **License:** MIT
- **Note:** Run LLaMA, Mistral, others locally with simple CLI.

### vLLM
- **URL:** https://github.com/vllm-project/vllm
- **Type:** Inference Engine
- **License:** Apache 2.0
- **Note:** High-throughput serving with PagedAttention.

### Text Generation Inference (TGI)
- **URL:** https://github.com/huggingface/text-generation-inference
- **Type:** Inference Server
- **Maintainer:** Hugging Face
- **License:** Apache 2.0
- **Note:** Production-ready LLM serving with streaming.

### llama.cpp
- **URL:** https://github.com/ggerganov/llama.cpp
- **Type:** Inference Engine
- **License:** MIT
- **Note:** C++ implementation for CPU/Metal/GPU inference.

### Candle
- **URL:** https://github.com/huggingface/candle
- **Type:** Framework
- **Maintainer:** Hugging Face
- **License:** Apache 2.0 / MIT
- **Note:** Minimalist ML framework in Rust.

---

## 🔗 LLM Application Frameworks

### LangChain
- **URL:** https://github.com/langchain-ai/langchain
- **Type:** Framework
- **License:** MIT
- **Note:** Building applications with LLMs (chains, agents, memory).

### LlamaIndex (GPT Index)
- **URL:** https://github.com/run-llama/llama_index
- **Type:** Framework
- **License:** MIT
- **Note:** Data framework for LLM applications (RAG, indexing).

### Semantic Kernel
- **URL:** https://github.com/microsoft/semantic-kernel
- **Type:** SDK
- **Maintainer:** Microsoft
- **License:** MIT
- **Note:** Integrate LLMs into apps (C#, Python, Java).

### Haystack
- **URL:** https://github.com/deepset-ai/haystack
- **Type:** Framework
- **License:** Apache 2.0
- **Note:** NLP framework with LLM support, RAG pipelines.

### Guidance
- **URL:** https://github.com/guidance-ai/guidance
- **Type:** Library
- **License:** MIT
- **Note:** Control LLM generation with structured prompts.

---

## 🤖 Agent Frameworks

### AutoGPT
- **URL:** https://github.com/Significant-Gravitas/AutoGPT
- **Type:** Agent Framework
- **License:** MIT
- **Note:** Autonomous GPT-4 agent with memory and tool use.

### BabyAGI
- **URL:** https://github.com/yoheinakajima/babyagi
- **Type:** Agent Framework
- **License:** MIT
- **Note:** Simple task-driven autonomous agent.

### AgentGPT
- **URL:** https://github.com/reworkd/AgentGPT
- **Type:** Agent Platform
- **License:** GPL-3.0
- **Note:** Browser-based autonomous AI agents.

### LangGraph
- **URL:** https://github.com/langchain-ai/langgraph
- **Type:** Framework
- **Maintainer:** LangChain
- **License:** MIT
- **Note:** Build multi-actor applications with cycles and controllability.

### CrewAI
- **URL:** https://github.com/joaomdmoura/crewai
- **Type:** Framework
- **License:** MIT
- **Note:** Orchestrate role-playing autonomous AI agents.

---

## 💬 Chatbot & UI Frameworks

### Gradio
- **URL:** https://github.com/gradio-app/gradio
- **Type:** UI Framework
- **License:** Apache 2.0
- **Note:** Build web UIs for ML models quickly.

### Streamlit
- **URL:** https://github.com/streamlit/streamlit
- **Type:** UI Framework
- **License:** Apache 2.0
- **Note:** Python app framework for data/ML apps.

### Chainlit
- **URL:** https://github.com/Chainlit/chainlit
- **Type:** UI Framework
- **License:** Apache 2.0
- **Note:** Build conversational AI interfaces.

### Text Generation WebUI
- **URL:** https://github.com/oobabooga/text-generation-webui
- **Type:** Web UI
- **License:** AGPL-3.0
- **Note:** Gradio-based UI for LLM inference.

---

## 🧮 Quantization Tools

### bitsandbytes
- **URL:** https://github.com/TimDettmers/bitsandbytes
- **Type:** Library
- **License:** MIT
- **Note:** 8-bit and 4-bit quantization for PyTorch.

### GPTQ
- **URL:** https://github.com/IST-DASLab/gptq
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Post-training quantization for GPT models.

### AutoGPTQ
- **URL:** https://github.com/PanQiWei/AutoGPTQ
- **Type:** Library
- **License:** MIT
- **Note:** Easy-to-use GPTQ quantization.

### GGML / GGUF
- **URL:** https://github.com/ggerganov/ggml
- **Type:** Library
- **License:** MIT
- **Note:** Tensor library for machine learning (used in llama.cpp).

### AWQ: Activation-aware Weight Quantization
- **URL:** https://github.com/mit-han-lab/llm-awq
- **Type:** Library
- **License:** MIT
- **Note:** Efficient low-bit weight quantization.

---

## 🔍 Vector Databases

### Chroma
- **URL:** https://github.com/chroma-core/chroma
- **Type:** Vector Database
- **License:** Apache 2.0
- **Note:** AI-native embedding database.

### Weaviate
- **URL:** https://github.com/weaviate/weaviate
- **Type:** Vector Database
- **License:** BSD 3-Clause
- **Note:** Open-source vector search engine.

### Qdrant
- **URL:** https://github.com/qdrant/qdrant
- **Type:** Vector Database
- **License:** Apache 2.0
- **Note:** Vector similarity search engine in Rust.

### Milvus
- **URL:** https://github.com/milvus-io/milvus
- **Type:** Vector Database
- **License:** Apache 2.0
- **Note:** Cloud-native vector database for embeddings.

### FAISS
- **URL:** https://github.com/facebookresearch/faiss
- **Type:** Library
- **Maintainer:** Meta AI
- **License:** MIT
- **Note:** Efficient similarity search and clustering.

### Pinecone (Free Tier)
- **URL:** https://www.pinecone.io/
- **Type:** Vector Database (SaaS)
- **Note:** Managed vector database with free tier.

---

## 🐍 Python LLM Libraries

### OpenAI Python SDK
- **URL:** https://github.com/openai/openai-python
- **Type:** SDK
- **License:** MIT
- **Note:** Official OpenAI API client.

### Anthropic SDK
- **URL:** https://github.com/anthropics/anthropic-sdk-python
- **Type:** SDK
- **License:** MIT
- **Note:** Official Claude API client.

### LiteLLM
- **URL:** https://github.com/BerriAI/litellm
- **Type:** Library
- **License:** MIT
- **Note:** Unified interface for 100+ LLM APIs.

### llm by Simon Willison
- **URL:** https://github.com/simonw/llm
- **Type:** CLI Tool
- **License:** Apache 2.0
- **Note:** Command-line tool for LLMs (local and API).

---

## 🧪 Evaluation & Benchmarking

### lm-evaluation-harness
- **URL:** https://github.com/EleutherAI/lm-evaluation-harness
- **Type:** Framework
- **Maintainer:** EleutherAI
- **License:** MIT
- **Note:** Unified LLM evaluation across benchmarks.

### OpenAI Evals
- **URL:** https://github.com/openai/evals
- **Type:** Framework
- **License:** MIT
- **Note:** Evaluation framework for LLMs.

### DeepEval
- **URL:** https://github.com/confident-ai/deepeval
- **Type:** Framework
- **License:** Apache 2.0
- **Note:** Unit testing framework for LLM applications.

---

## 📊 Observability & Monitoring

### LangSmith
- **URL:** https://smith.langchain.com/
- **Type:** Platform
- **Maintainer:** LangChain
- **Note:** Debugging and monitoring LLM applications (free tier).

### Weights & Biases
- **URL:** https://wandb.ai/
- **Type:** Platform
- **Note:** Experiment tracking for ML (free for open-source).

### TensorBoard
- **URL:** https://www.tensorflow.org/tensorboard
- **Type:** Visualization Tool
- **License:** Apache 2.0
- **Note:** Training visualization and profiling.

---

## 🚀 Additional Tools

### Axolotl
- **URL:** https://github.com/OpenAccess-AI-Collective/axolotl
- **Type:** Fine-tuning Tool
- **License:** Apache 2.0
- **Note:** Streamlined LLM fine-tuning with various techniques.

### LM Studio
- **URL:** https://lmstudio.ai/
- **Type:** Desktop App
- **License:** Free (Proprietary)
- **Note:** Run local LLMs with GUI (Windows/Mac/Linux).

### GPT4All
- **URL:** https://github.com/nomic-ai/gpt4all
- **Type:** Framework + UI
- **License:** MIT
- **Note:** Run LLMs locally on consumer hardware.
