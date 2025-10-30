# 📖 LLM Engineering Glossary

**Comprehensive glossary of terms, acronyms, and concepts** in Large Language Model engineering.

---

## 📑 Navigation

- [A](#a) | [B](#b) | [C](#c) | [D](#d) | [E](#e) | [F](#f) | [G](#g) | [H](#h) | [I](#i) | [J](#j) | [K](#k) | [L](#l) | [M](#m)
- [N](#n) | [O](#o) | [P](#p) | [Q](#q) | [R](#r) | [S](#s) | [T](#t) | [U](#u) | [V](#v) | [W](#w) | [X](#x) | [Y](#y) | [Z](#z)

---

## A

**Agent**: An LLM-powered system that can take actions, use tools, and make decisions autonomously to accomplish tasks.

**ALiBi (Attention with Linear Biases)**: Position encoding method that enables length extrapolation (handling sequences longer than training).

**Alignment**: Process of making LLM outputs match human values and intentions, often through RLHF.

**Attention Mechanism**: Core component of transformers that weighs importance of different parts of input when generating output.

**Autoregressive**: Generating tokens sequentially, where each token depends on previously generated tokens (used in GPT models).

**AWQ (Activation-aware Weight Quantization)**: Quantization method that considers activation patterns for better quality.

---

## B

**Batch Size**: Number of examples processed simultaneously during training or inference.

**BERT (Bidirectional Encoder Representations from Transformers)**: Encoder-only model good for understanding tasks (classification, NER).

**Bias**: Undesirable prejudices in model outputs, or mathematical bias term in neural networks.

**BLEU (Bilingual Evaluation Understudy)**: Metric for evaluating machine translation quality.

**BPE (Byte Pair Encoding)**: Tokenization algorithm that breaks text into subword units.

**Byte-level Encoding**: Tokenization that operates on raw bytes rather than characters.

---

## C

**Causality/Causal Mask**: In transformers, preventing attention to future tokens (left-to-right only).

**Chain-of-Thought (CoT)**: Prompting technique where model shows reasoning steps before final answer.

**Checkpoint**: Saved model weights at a specific training step.

**Chunking**: Splitting long documents into smaller pieces for RAG/embedding.

**Claude**: Family of LLMs by Anthropic (Claude 1, 2, 3).

**Context Length/Context Window**: Maximum number of tokens model can process at once (e.g., 4K, 32K, 200K).

**Constitutional AI**: Alignment method using AI feedback and principles (developed by Anthropic).

**Continuous Batching**: Dynamically batching requests for higher throughput in inference.

**Cross-Entropy Loss**: Standard loss function for training language models.

---

## D

**Decoder**: Transformer component that generates text autoregressively (used in GPT).

**DeepSpeed**: Microsoft's training optimization library for large models.

**Distillation**: Training smaller model to mimic larger model's behavior.

**DPO (Direct Preference Optimization)**: Alternative to PPO for RLHF, simpler and more stable.

**Dropout**: Regularization technique randomly disabling neurons during training.

---

## E

**Embeddings**: Dense vector representations of text that capture semantic meaning.

**Encoder**: Transformer component that processes input bidirectionally (used in BERT).

**Epoch**: One complete pass through entire training dataset.

**Evaluation/Eval**: Testing model performance on benchmarks or custom metrics.

**Exploding Gradients**: Training instability where gradients become too large.

---

## F

**FAISS (Facebook AI Similarity Search)**: Library for efficient similarity search in high dimensions.

**Few-shot Learning**: Providing model with few examples in prompt before task.

**Fine-tuning**: Further training pre-trained model on specific task/domain.

**FLAN**: Google's instruction-tuning methodology and dataset collection.

**Flash Attention**: Optimized attention implementation that's faster and more memory-efficient.

**FP16/FP32**: Floating-point precision (16-bit vs 32-bit). FP16 uses less memory.

**FSDP (Fully Sharded Data Parallel)**: PyTorch's distributed training method.

---

## G

**Gemini**: Google's family of multimodal LLMs.

**Gemma**: Google's open-source LLMs (2B, 7B).

**Generative AI**: AI that creates new content (text, images, code).

**GGUF**: File format for quantized models used by llama.cpp.

**GPT (Generative Pre-trained Transformer)**: OpenAI's family of decoder-only models.

**GPTQ**: Post-training quantization method for LLMs.

**Gradient**: Derivative showing direction to adjust weights during training.

**Gradient Accumulation**: Simulating larger batches by accumulating gradients over multiple steps.

**Gradient Checkpointing**: Trading compute for memory by recomputing activations.

**Greedy Decoding**: Always selecting most probable next token (deterministic).

**GQA (Grouped Query Attention)**: Memory-efficient attention variant in Mistral.

---

## H

**Hallucination**: Model generating plausible-sounding but incorrect information.

**HumanEval**: Benchmark for evaluating code generation (164 Python problems).

**Hugging Face**: Company/platform providing model hosting, libraries (Transformers, PEFT).

**Hybrid Search**: Combining keyword search (BM25) with semantic search for better retrieval.

**Hyperparameters**: Configuration values for training (learning rate, batch size, etc.).

---

## I

**Inference**: Using trained model to generate outputs (vs. training).

**Instruction Tuning**: Fine-tuning model to follow instructions (like "Summarize this...").

**INT4/INT8**: Integer quantization (4-bit or 8-bit), reduces model size.

---

## K

**KV Cache**: Storing key-value pairs from previous tokens to speed up inference.

**k-bit Quantization**: Reducing weight precision to k bits (e.g., 4-bit, 8-bit).

---

## L

**LangChain**: Framework for building LLM applications with chains, agents, memory.

**LangSmith**: LangChain's debugging and monitoring platform.

**Latency**: Time delay between input and output.

**Layer Normalization**: Normalization technique used in transformers.

**Learning Rate**: Step size for weight updates during training.

**LLaMA (Large Language Model Meta AI)**: Meta's family of open LLMs (7B-70B).

**LlamaIndex**: Framework focused on RAG and data indexing.

**LLM (Large Language Model)**: AI models trained on vast text to understand/generate language.

**LoRA (Low-Rank Adaptation)**: Efficient fine-tuning by updating small matrices.

**Loss Function**: Measures difference between predictions and actual values.

---

## M

**Masked Language Modeling (MLM)**: Training objective in BERT (predict masked tokens).

**Megatron-LM**: NVIDIA's framework for training massive models.

**MHA (Multi-Head Attention)**: Standard attention with multiple parallel attention heads.

**Mistral**: French AI company and their open-source 7B model.

**Mixture of Experts (MoE)**: Architecture with multiple expert networks (used in Mixtral).

**MMLU (Massive Multitask Language Understanding)**: Benchmark testing knowledge across 57 subjects.

**Modal**: Serverless platform for deploying ML models.

**Model Compression**: Reducing model size via quantization, pruning, distillation.

**Multi-modal**: Models handling multiple input types (text, images, audio).

**Multi-turn Conversation**: Dialogue with memory of previous exchanges.

---

## N

**NLP (Natural Language Processing)**: Field of AI dealing with human language.

**Nucleus Sampling**: Sampling from top-p probability mass (vs top-k tokens).

**NVIDIA**: GPU manufacturer; makes A100, H100 GPUs for AI training.

---

## O

**Ollama**: Tool for running LLMs locally with simple CLI.

**One-shot Learning**: Providing one example in prompt.

**OpenAI**: Company behind GPT models and ChatGPT.

**Overfit**: Model memorizing training data instead of learning general patterns.

---

## P

**PagedAttention**: Memory optimization in vLLM for efficient inference.

**Parameters**: Learnable weights in neural network (e.g., 7B = 7 billion parameters).

**PEFT (Parameter-Efficient Fine-Tuning)**: Methods like LoRA that update few parameters.

**Perplexity**: Metric measuring model's uncertainty (lower is better).

**Phi**: Microsoft's small efficient models (Phi-1, Phi-2, Phi-3).

**Position Encoding**: Adding position information to tokens (absolute, RoPE, ALiBi).

**PPO (Proximal Policy Optimization)**: RL algorithm used in RLHF.

**Pre-training**: Initial training on large corpus before fine-tuning.

**Prompt**: Input text guiding LLM's response.

**Prompt Engineering**: Crafting effective prompts for desired outputs.

**Prompt Template**: Reusable prompt structure with placeholders.

**Pruning**: Removing unnecessary weights to compress model.

---

## Q

**QLoRA**: LoRA + 4-bit quantization for memory-efficient fine-tuning.

**Quantization**: Reducing numerical precision (FP16→INT8→INT4) to save memory.

**Query**: In attention, the "question" vector searching for relevant keys.

---

## R

**RAG (Retrieval-Augmented Generation)**: Retrieving relevant docs to augment LLM's context.

**RANK**: Position in sorted list (used in reranking).

**ReAct**: Prompting pattern combining Reasoning and Actions.

**Reinforcement Learning from Human Feedback (RLHF)**: Training models using human preferences.

**Reranking**: Re-ordering retrieved results using more sophisticated model.

**RoPE (Rotary Position Embedding)**: Position encoding method (used in LLaMA).

**Rouge**: Metric for evaluating summarization quality.

---

## S

**Sampling**: Randomly selecting next token based on probability distribution.

**Scaling Laws**: Relationships between model size, data, compute, and performance.

**Self-Attention**: Core mechanism where tokens attend to other tokens.

**Semantic Search**: Finding similar meanings (vs keyword matching).

**SentencePiece**: Tokenization library (used in LLaMA, T5).

**Sequence Length**: Number of tokens in input/output.

**Softmax**: Function converting logits to probability distribution.

**Sparse**: Most values are zero (vs dense). Used in MoE.

**SQuAD**: Reading comprehension benchmark dataset.

**STEM**: Science, Technology, Engineering, Mathematics.

**Supervised Fine-Tuning (SFT)**: Fine-tuning with labeled examples.

---

## T

**T5 (Text-to-Text Transfer Transformer)**: Google's encoder-decoder model.

**Temperature**: Randomness control in sampling (0=deterministic, 2=very random).

**Tensor**: Multi-dimensional array (fundamental data structure).

**Tensor Parallelism**: Splitting model layers across multiple GPUs.

**TensorRT**: NVIDIA's inference optimization SDK.

**Text Generation Inference (TGI)**: Hugging Face's production inference server.

**TF-IDF**: Traditional text similarity metric (term frequency-inverse document frequency).

**Throughput**: Number of tokens/requests processed per second.

**tiktoken**: OpenAI's fast tokenizer library.

**Token**: Basic unit of text (word piece, subword, or character).

**Tokenization**: Converting text into tokens.

**Top-k Sampling**: Sampling from k most probable tokens.

**Top-p Sampling**: Sampling from tokens with cumulative probability p (nucleus sampling).

**Transfer Learning**: Using pre-trained model for new task.

**Transformer**: Neural architecture using attention (basis of modern LLMs).

**TRL (Transformer Reinforcement Learning)**: Hugging Face's RLHF library.

**Truncation**: Cutting text to fit maximum length.

---

## U

**Unigram**: Tokenization algorithm treating each token independently.

**Unsupervised Learning**: Training without labeled data.

---

## V

**Vanishing Gradients**: Training issue where gradients become too small.

**Vector Database**: Database optimized for similarity search (Pinecone, Chroma, Qdrant).

**Vector Embeddings**: Numerical representations of text in high-dimensional space.

**vLLM**: High-throughput inference engine for LLMs.

---

## W

**Weights**: Parameters in neural network that are learned during training.

**Weights & Biases (W&B)**: Experiment tracking platform.

**Window Size**: Context length or attention span.

**WordPiece**: Tokenization algorithm (used in BERT).

---

## X

**XNLI**: Cross-lingual natural language inference benchmark.

---

## Z

**Zero-shot Learning**: Performing task without any examples in prompt.

**ZeRO**: Memory optimization in DeepSpeed (ZeRO-1, ZeRO-2, ZeRO-3).

---

## Common Acronyms Quick Reference

| Acronym | Full Form | Category |
|---------|-----------|----------|
| **AI** | Artificial Intelligence | General |
| **AGI** | Artificial General Intelligence | Concept |
| **API** | Application Programming Interface | Technology |
| **BERT** | Bidirectional Encoder Representations from Transformers | Model |
| **BPE** | Byte Pair Encoding | Tokenization |
| **CoT** | Chain-of-Thought | Prompting |
| **DL** | Deep Learning | Field |
| **DPO** | Direct Preference Optimization | Training |
| **FP16/32** | Floating Point 16/32-bit | Precision |
| **FSDP** | Fully Sharded Data Parallel | Training |
| **GPT** | Generative Pre-trained Transformer | Model |
| **GPU** | Graphics Processing Unit | Hardware |
| **GQA** | Grouped Query Attention | Architecture |
| **INT4/8** | Integer 4/8-bit | Quantization |
| **KV** | Key-Value | Attention |
| **LLM** | Large Language Model | Model |
| **LoRA** | Low-Rank Adaptation | Fine-tuning |
| **MHA** | Multi-Head Attention | Architecture |
| **ML** | Machine Learning | Field |
| **MLOps** | Machine Learning Operations | Practice |
| **MMLU** | Massive Multitask Language Understanding | Benchmark |
| **MoE** | Mixture of Experts | Architecture |
| **NER** | Named Entity Recognition | Task |
| **NLP** | Natural Language Processing | Field |
| **PEFT** | Parameter-Efficient Fine-Tuning | Method |
| **PPO** | Proximal Policy Optimization | Training |
| **QLoRA** | Quantized LoRA | Fine-tuning |
| **RAG** | Retrieval-Augmented Generation | Architecture |
| **RL** | Reinforcement Learning | Method |
| **RLHF** | Reinforcement Learning from Human Feedback | Training |
| **RoPE** | Rotary Position Embedding | Architecture |
| **SFT** | Supervised Fine-Tuning | Training |
| **SWA** | Sliding Window Attention | Architecture |
| **TGI** | Text Generation Inference | Serving |
| **TPU** | Tensor Processing Unit | Hardware |
| **TRL** | Transformer Reinforcement Learning | Library |
| **vLLM** | High-throughput LLM serving | Serving |
| **VRAM** | Video RAM (GPU memory) | Hardware |

---

## Model Families Quick Reference

| Family | Company | Type | Notable Models |
|--------|---------|------|----------------|
| **GPT** | OpenAI | Closed | GPT-3.5, GPT-4, GPT-4 Turbo |
| **Claude** | Anthropic | Closed | Claude 1, 2, 3 (Opus, Sonnet, Haiku) |
| **Gemini** | Google | Closed | Gemini Pro, Ultra |
| **LLaMA** | Meta | Open | LLaMA 1, LLaMA 2 (7B-70B) |
| **Mistral** | Mistral AI | Open | Mistral 7B, Mixtral 8x7B |
| **Gemma** | Google | Open | Gemma 2B, 7B |
| **Phi** | Microsoft | Open | Phi-1, Phi-2, Phi-3 |
| **Qwen** | Alibaba | Open | Qwen 7B-72B |
| **Yi** | 01.AI | Open | Yi 6B-34B |
| **Falcon** | TII UAE | Open | Falcon 7B-180B |

---

## 📚 Related Resources

- **Detailed Explanations**: See category READMEs
- **Practical Guide**: [QUICKSTART.md](./QUICKSTART.md)
- **Common Questions**: [FAQ.md](./FAQ.md)

---

**Confused about a term?**
- Search this glossary (Ctrl+F)
- Check [FAQ.md](./FAQ.md)
- Ask in [Community](./13-Community/)

**Last Updated:** October 2025
