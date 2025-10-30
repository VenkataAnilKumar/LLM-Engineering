# ❓ Frequently Asked Questions (FAQ)

Common questions about LLM Engineering, answered concisely.

---

## 📑 Table of Contents

1. [Getting Started](#getting-started)
2. [Models & Architecture](#models--architecture)
3. [Training & Fine-Tuning](#training--fine-tuning)
4. [Prompting & Usage](#prompting--usage)
5. [RAG & Applications](#rag--applications)
6. [Deployment & Production](#deployment--production)
7. [Costs & Resources](#costs--resources)
8. [Career & Learning](#career--learning)

---

## Getting Started

### Q: What prerequisites do I need to start with LLMs?
**A:** Basic Python programming and command line usage. No ML background strictly required, but helpful. Math (linear algebra, calculus) useful for deep understanding but not essential for application development.

### Q: Should I learn ML/DL before LLMs?
**A:** For **application development**: No, start directly with LLMs. For **model development/research**: Yes, take Andrew Ng's ML course + Deep Learning Specialization first.

### Q: Do I need a GPU?
**A:** 
- **For learning**: No, use Google Colab (free GPU) or Ollama (CPU)
- **For development**: Helpful but not required
- **For fine-tuning**: Yes, but use Colab or cloud GPUs
- **For deployment**: Depends on scale and latency requirements

### Q: What's the best free way to experiment with LLMs?
**A:**
1. **Cloud**: Google Colab (free GPU), Hugging Face Spaces
2. **Local**: Ollama with 7B models (runs on CPU)
3. **APIs**: OpenAI/Anthropic free tiers (limited)

---

## Models & Architecture

### Q: What's the difference between GPT, BERT, and T5?
**A:**
- **GPT (GPT-2, GPT-3, GPT-4)**: Decoder-only, autoregressive (predict next token). Best for generation.
- **BERT**: Encoder-only, bidirectional. Best for classification, understanding.
- **T5**: Encoder-decoder. Versatile, treats everything as text-to-text.

For modern LLM applications, focus on decoder-only models (GPT-style, LLaMA, Mistral).

### Q: Which model should I use for my project?
**A:**
| Use Case | Recommended Model |
|----------|-------------------|
| Learning/prototyping | LLaMA 2 7B (Ollama) |
| Production chat | GPT-4, Claude 3, or Mistral 7B |
| Code generation | GPT-4, Claude 3, or CodeLLaMA |
| Local/private | LLaMA 2, Mistral, or Phi-2 |
| Budget-constrained | Mistral 7B or Phi-2 |
| Maximum performance | GPT-4 or Claude 3 Opus |

### Q: What's the difference between parameters (7B, 13B, 70B)?
**A:** Number of learnable weights. More parameters generally = better performance but:
- **7B**: Fast, runs on consumer hardware, good for most tasks
- **13-34B**: Better reasoning, still manageable
- **70B+**: Best performance, requires significant resources

### Q: Open-source vs Closed-source models?
**A:**
| Aspect | Open-source (LLaMA, Mistral) | Closed (GPT-4, Claude) |
|--------|------------------------------|------------------------|
| Cost | Free (compute only) | Pay per token |
| Privacy | Run locally | Data sent to API |
| Customization | Full control | Limited |
| Performance | Good (7-70B range) | Best |
| Ease of use | Moderate setup | Very easy (API) |

---

## Training & Fine-Tuning

### Q: What's the difference between pre-training, fine-tuning, and RLHF?
**A:**
- **Pre-training**: Training from scratch on huge datasets (expensive, rarely needed)
- **Fine-tuning**: Adapting pre-trained model to specific task (moderate cost)
- **RLHF**: Aligning model with human preferences (expensive, research-level)

For most projects, start with fine-tuning or even just good prompting.

### Q: Should I fine-tune or use RAG?
**A:**
| Use RAG when | Use Fine-tuning when |
|--------------|----------------------|
| Data changes frequently | Need specific style/tone |
| Need source citations | Pattern is learnable |
| Limited training budget | Have quality training data |
| External knowledge needed | Want faster inference |

**Best**: Often combine both (RAG + fine-tuned model).

### Q: How much does fine-tuning cost?
**A:**
- **LoRA on 7B**: ~$5-20 (few hours on A100)
- **QLoRA on 7B**: Can run on free Colab
- **Full fine-tune 7B**: $50-200
- **Full fine-tune 70B**: $1000+

Use QLoRA for budget-friendly fine-tuning.

### Q: How much data do I need for fine-tuning?
**A:**
- **Minimum**: 100-500 examples
- **Good**: 1,000-10,000 examples
- **Excellent**: 10,000+ examples

Quality matters more than quantity. 500 high-quality examples > 5,000 low-quality.

### Q: What's LoRA and QLoRA?
**A:**
- **LoRA**: Low-Rank Adaptation - updates only small matrices, 100x cheaper than full fine-tuning
- **QLoRA**: LoRA + 4-bit quantization - runs on consumer GPUs (24GB VRAM)

Both give ~90-95% of full fine-tuning quality at fraction of cost.

---

## Prompting & Usage

### Q: What's prompt engineering?
**A:** Crafting inputs to get desired outputs from LLMs. Techniques:
- **Zero-shot**: No examples, just instruction
- **Few-shot**: Include 2-5 examples
- **Chain-of-Thought**: "Let's think step by step"
- **ReAct**: Reasoning + Action pattern

### Q: How do I reduce hallucinations?
**A:**
1. Use **RAG** to ground responses in facts
2. Add "If you don't know, say so" to prompts
3. Use **lower temperature** (0.1-0.3)
4. Request **citations/sources**
5. Implement **validation** logic
6. Use **better models** (GPT-4 > GPT-3.5)

### Q: What's temperature and top_p?
**A:**
- **Temperature (0-2)**: Randomness. 0 = deterministic, 1 = balanced, 2 = creative
  - Use 0.1-0.3 for factual tasks
  - Use 0.7-1.0 for creative tasks
- **Top_p (0-1)**: Nucleus sampling. 0.9 = consider top 90% probable tokens
  - Usually keep at 0.9-1.0

### Q: How long can the context be?
**A:** Varies by model:
- GPT-3.5: 16K tokens (~12K words)
- GPT-4: 128K tokens (~96K words)
- Claude 3: 200K tokens (~150K words)
- LLaMA 2: 4K tokens (extended to 32K+)
- Mistral: 32K tokens

1 token ≈ 0.75 words in English.

---

## RAG & Applications

### Q: What is RAG?
**A:** Retrieval-Augmented Generation: 
1. Retrieve relevant documents from database
2. Augment prompt with retrieved context
3. Generate answer using LLM

Prevents hallucinations, enables private/updated knowledge.

### Q: Which vector database should I use?
**A:**
| Database | Best For |
|----------|----------|
| Chroma | Development, prototyping |
| Qdrant | Production, complex filtering |
| Pinecone | Managed service, easy scaling |
| Weaviate | Multi-modal, graph features |
| FAISS | Research, local similarity search |

Start with Chroma, move to Qdrant/Pinecone for production.

### Q: What's the best chunk size for RAG?
**A:** 
- **Start with**: 512-1024 tokens
- **Smaller (256-512)**: More precise retrieval, more chunks
- **Larger (1024-2048)**: More context, fewer chunks
- **Best practice**: Test multiple sizes, use overlap (50-100 tokens)

### Q: How do I improve RAG accuracy?
**A:**
1. **Better retrieval**: Hybrid search (keyword + semantic)
2. **Reranking**: Use ColBERT or cross-encoder
3. **Query transformation**: Rephrase, expand queries
4. **Better chunking**: Semantic or recursive splitters
5. **Metadata filtering**: Filter by date, source, etc.
6. **Parent document**: Retrieve with chunks, return full documents

---

## Deployment & Production

### Q: How do I deploy an LLM application?
**A:**
**Options:**
1. **API-based**: OpenAI/Anthropic API (easiest)
2. **Self-hosted**: vLLM/TGI on cloud GPU (control)
3. **Local**: Ollama for on-premise (privacy)
4. **Serverless**: Modal, Banana, Replicate (auto-scaling)

**Tech stack example:**
- Frontend: Streamlit/Gradio
- Backend: FastAPI
- LLM: Ollama (dev) → vLLM (prod)
- Vector DB: Chroma (dev) → Qdrant (prod)

### Q: What's the difference between vLLM, TGI, and Ollama?
**A:**
| Framework | Best For | Performance | Ease |
|-----------|----------|-------------|------|
| **vLLM** | High-throughput production | ⚡⚡⚡⚡⚡ | 🟡 Medium |
| **TGI** | HF models, streaming | ⚡⚡⚡⚡ | 🟢 Easy |
| **Ollama** | Local dev, single-user | ⚡⚡⚡ | 🟢 Very Easy |
| **llama.cpp** | CPU/edge deployment | ⚡⚡ | 🟡 Medium |

### Q: How do I reduce inference costs?
**A:**
1. **Use smaller models**: 7B instead of 70B when possible
2. **Quantize**: INT8/INT4 (2-4x cheaper, minimal quality loss)
3. **Batch requests**: Group queries together
4. **Cache responses**: Semantic cache for similar queries
5. **Use spot instances**: 60-80% cheaper on cloud
6. **Optimize prompts**: Shorter prompts = fewer tokens
7. **Local hosting**: One-time setup vs per-token costs

### Q: How much does it cost to run an LLM in production?
**A:**
**API-based (GPT-4):**
- 1M tokens input: $10
- 1M tokens output: $30
- ~1K users, 10 msgs/day: $500-2000/mo

**Self-hosted (7B on GPU):**
- GPU server (A100): $1.50-3/hour = $1000-2000/mo
- Serverless (pay per use): $0.0002-0.001/second
- Consumer GPU (local): One-time hardware cost

---

## Costs & Resources

### Q: Can I run LLMs without spending money?
**A:** Yes!
- **Free compute**: Google Colab, Kaggle Notebooks
- **Free APIs**: OpenAI/Anthropic free tiers (limited)
- **Local (CPU)**: Ollama with 7B models
- **Free hosting**: Hugging Face Spaces, Streamlit Cloud

### Q: What GPU do I need?
**A:**
| Model Size | Minimum GPU | Recommended |
|------------|-------------|-------------|
| 7B (INT4) | 6GB | 8GB+ |
| 7B (FP16) | 14GB | 16GB+ |
| 13B (INT4) | 8GB | 12GB+ |
| 13B (FP16) | 26GB | 32GB+ |
| 70B (INT4) | 40GB | 48GB+ |

For fine-tuning, add 50-100% more VRAM.

**Budget options:**
- NVIDIA RTX 3090/4090 (24GB)
- Cloud: RunPod, Lambda Labs ($0.50-1/hour)

---

## Career & Learning

### Q: How long does it take to become an LLM engineer?
**A:**
- **Basic applications**: 1-2 months
- **Production-ready**: 3-6 months
- **Expert level**: 1-2 years

Depends on prior ML/programming experience.

### Q: What jobs are available in LLM space?
**A:**
- **LLM Application Developer**: Build applications using LLMs
- **Prompt Engineer**: Optimize prompts for businesses
- **ML Engineer (LLM focus)**: Fine-tune, deploy, optimize models
- **AI Research Scientist**: Develop new LLM architectures
- **MLOps Engineer**: Infrastructure for LLM deployment

### Q: What's the best learning path?
**A:**
See [QUICKSTART.md](./QUICKSTART.md) for detailed 30-day plan.

**Quick version:**
1. **Month 1**: Basics + Prompting
2. **Month 2**: RAG + Applications
3. **Month 3**: Fine-tuning + Deployment
4. **Month 4+**: Specialize (agents, optimization, research)

### Q: Are LLMs just a hype? Will they replace programmers?
**A:**
- **Hype?** No, transformative technology with real applications
- **Replace programmers?** No, augment productivity 10-100x
- **Future**: Coding becomes more high-level, LLMs handle boilerplate

LLMs are tool multipliers, not replacements.

---

## Troubleshooting

### Q: "CUDA out of memory" error
**A:**
1. Use smaller model or batch size
2. Enable gradient checkpointing
3. Use QLoRA instead of full fine-tuning
4. Clear GPU cache: `torch.cuda.empty_cache()`
5. Use Colab with high RAM

### Q: Model outputs gibberish
**A:**
- Check tokenizer matches model
- Verify prompt format (some models need special tokens)
- Try lower temperature
- Check if model loaded correctly
- Use chat templates for chat models

### Q: Slow inference
**A:**
1. Use quantized models (GGUF, GPTQ)
2. Enable GPU acceleration
3. Use vLLM or TGI for optimization
4. Reduce context length
5. Batch requests
6. Use smaller model if acceptable

---

## Additional Resources

- **More Questions?** Join [Discord communities](./13-Community/)
- **Hands-on Practice:** [QUICKSTART.md](./QUICKSTART.md)
- **Technical Terms:** [GLOSSARY.md](./GLOSSARY.md)
- **Learning Resources:** [09-Learning-Resources](./09-Learning-Resources/)

---

**Have a question not answered here?** 
- Open an issue on GitHub
- Ask in community forums
- Contribute via pull request

**Last Updated:** October 2025
