# 📄 Research Papers

**Essential research papers for LLM engineering**, organized by topic with summaries and key contributions.

---

## 📑 Table of Contents

- [Foundational Papers](#foundational-papers)
- [Transformer Architecture](#transformer-architecture)
- [Large Language Models](#large-language-models)
- [Fine-tuning & Adaptation](#fine-tuning--adaptation)
- [Prompt Engineering](#prompt-engineering)
- [Retrieval-Augmented Generation](#retrieval-augmented-generation)
- [Alignment & RLHF](#alignment--rlhf)
- [Efficient Training & Inference](#efficient-training--inference)
- [Evaluation & Benchmarking](#evaluation--benchmarking)
- [Multimodal Models](#multimodal-models)
- [Safety & Robustness](#safety--robustness)
- [Reading Lists by Role](#reading-lists-by-role)

---

## 🎯 Foundational Papers

### **Attention Is All You Need** (2017)
- **Authors**: Vaswani et al. (Google)
- **Link**: [arXiv](https://arxiv.org/abs/1706.03762) | 🟢 **Beginner** | ⏱️ 2 hours
- **Key Contribution**: Introduced the Transformer architecture with self-attention mechanism
- **Why Read**: Foundation of all modern LLMs (GPT, BERT, T5, LLaMA)
- **Key Concepts**: Multi-head attention, positional encoding, encoder-decoder architecture

### **BERT: Pre-training of Deep Bidirectional Transformers** (2018)
- **Authors**: Devlin et al. (Google)
- **Link**: [arXiv](https://arxiv.org/abs/1810.04805) | 🟢 **Beginner** | ⏱️ 1.5 hours
- **Key Contribution**: Bidirectional pre-training with masked language modeling
- **Impact**: Revolutionized NLP tasks (classification, NER, QA)
- **Key Concepts**: MLM, next sentence prediction, transfer learning

### **Language Models are Unsupervised Multitask Learners (GPT-2)** (2019)
- **Authors**: Radford et al. (OpenAI)
- **Link**: [PDF](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) | 🟢 **Beginner** | ⏱️ 1 hour
- **Key Contribution**: Demonstrated zero-shot learning capabilities at scale
- **Impact**: Showed LLMs can generalize without task-specific training
- **Key Concepts**: Zero-shot learning, generative pre-training

---

## 🏗️ Transformer Architecture

### **Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context** (2019)
- **Authors**: Dai et al. (Google/CMU)
- **Link**: [arXiv](https://arxiv.org/abs/1901.02860) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: Segment-level recurrence for longer context
- **Innovation**: Relative positional encodings

### **Reformer: The Efficient Transformer** (2020)
- **Authors**: Kitaev et al. (Google)
- **Link**: [arXiv](https://arxiv.org/abs/2001.04451) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: Locality-sensitive hashing for efficient attention
- **Impact**: Reduced memory from O(L²) to O(L log L)

### **Flash Attention: Fast and Memory-Efficient Exact Attention** (2022)
- **Authors**: Dao et al. (Stanford)
- **Link**: [arXiv](https://arxiv.org/abs/2205.14135) | 🔴 **Advanced** | ⏱️ 3 hours
- **Key Contribution**: IO-aware attention algorithm
- **Impact**: 2-4x speedup, enables longer sequences
- **Used By**: Most modern LLM training (LLaMA, Mistral)

---

## 🤖 Large Language Models

### **Language Models are Few-Shot Learners (GPT-3)** (2020)
- **Authors**: Brown et al. (OpenAI)
- **Link**: [arXiv](https://arxiv.org/abs/2005.14165) | 🟢 **Beginner** | ⏱️ 2 hours
- **Key Contribution**: 175B parameter model demonstrating in-context learning
- **Impact**: Kickstarted the LLM revolution
- **Key Concepts**: Few-shot prompting, scaling laws, emergent abilities

### **Training Compute-Optimal Large Language Models (Chinchilla)** (2022)
- **Authors**: Hoffmann et al. (DeepMind)
- **Link**: [arXiv](https://arxiv.org/abs/2203.15556) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: Optimal model size vs training tokens ratio
- **Finding**: Models should be trained on 20x tokens as parameters
- **Impact**: Influenced LLaMA, Mistral training strategies

### **LLaMA: Open and Efficient Foundation Language Models** (2023)
- **Authors**: Touvron et al. (Meta)
- **Link**: [arXiv](https://arxiv.org/abs/2302.13971) | 🟢 **Beginner** | ⏱️ 1.5 hours
- **Key Contribution**: High-quality open models (7B-65B)
- **Impact**: Democratized LLM access, sparked open-source movement
- **Architecture**: RMSNorm, SwiGLU, RoPE

### **LLaMA 2: Open Foundation and Fine-Tuned Chat Models** (2023)
- **Authors**: Touvron et al. (Meta)
- **Link**: [arXiv](https://arxiv.org/abs/2307.09288) | 🟢 **Beginner** | ⏱️ 2 hours
- **Key Contribution**: Open commercial license + RLHF chat models
- **Impact**: Production-ready open models with safety alignment
- **Training**: Detailed RLHF process, 2 trillion tokens

### **Mistral 7B** (2023)
- **Authors**: Jiang et al. (Mistral AI)
- **Link**: [arXiv](https://arxiv.org/abs/2310.06825) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Sliding window attention + grouped query attention
- **Performance**: Outperforms LLaMA 2 13B while being smaller
- **Innovation**: Efficient architecture for longer context

### **Mixtral of Experts** (2024)
- **Authors**: Jiang et al. (Mistral AI)
- **Link**: [arXiv](https://arxiv.org/abs/2401.04088) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: Sparse mixture of experts (8x7B)
- **Innovation**: 47B parameters, only 13B active per token
- **Performance**: Matches/exceeds GPT-3.5 at lower cost

---

## 🎨 Fine-tuning & Adaptation

### **LoRA: Low-Rank Adaptation of Large Language Models** (2021)
- **Authors**: Hu et al. (Microsoft)
- **Link**: [arXiv](https://arxiv.org/abs/2106.09685) | 🟢 **Beginner** | ⏱️ 1.5 hours
- **Key Contribution**: Fine-tune by updating low-rank matrices
- **Impact**: Standard method for efficient fine-tuning
- **Savings**: 10,000x fewer trainable parameters, 3x less GPU memory

### **QLoRA: Efficient Finetuning of Quantized LLMs** (2023)
- **Authors**: Dettmers et al. (University of Washington)
- **Link**: [arXiv](https://arxiv.org/abs/2305.14314) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: LoRA + 4-bit quantization
- **Impact**: Fine-tune 65B models on single 48GB GPU
- **Innovations**: NormalFloat4, double quantization, paged optimizers

### **Prefix-Tuning: Optimizing Continuous Prompts** (2021)
- **Authors**: Li and Liang (Stanford)
- **Link**: [arXiv](https://arxiv.org/abs/2101.00190) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Learn continuous prompts instead of fine-tuning all weights
- **Use Case**: Alternative to LoRA for parameter-efficient tuning

### **Parameter-Efficient Transfer Learning for NLP** (2019)
- **Authors**: Houlsby et al. (Google)
- **Link**: [arXiv](https://arxiv.org/abs/1902.00751) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Adapter layers for efficient fine-tuning
- **Method**: Insert small trainable modules between transformer layers

---

## 💬 Prompt Engineering

### **Chain-of-Thought Prompting Elicits Reasoning** (2022)
- **Authors**: Wei et al. (Google)
- **Link**: [arXiv](https://arxiv.org/abs/2201.11903) | 🟢 **Beginner** | ⏱️ 1 hour
- **Key Contribution**: Adding reasoning steps improves complex task performance
- **Impact**: 3-5x improvement on math/reasoning benchmarks
- **Example**: "Let's think step by step..."

### **ReAct: Synergizing Reasoning and Acting in Language Models** (2022)
- **Authors**: Yao et al. (Princeton)
- **Link**: [arXiv](https://arxiv.org/abs/2210.03629) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Interleaving reasoning traces with actions
- **Impact**: Foundation for LLM agents (AutoGPT, BabyAGI)
- **Format**: Thought → Action → Observation loop

### **Tree of Thoughts: Deliberate Problem Solving** (2023)
- **Authors**: Yao et al. (Princeton)
- **Link**: [arXiv](https://arxiv.org/abs/2305.10601) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Explore multiple reasoning paths (tree search)
- **Use Case**: Complex problems requiring backtracking

### **Lost in the Middle: How Language Models Use Long Contexts** (2023)
- **Authors**: Liu et al. (Stanford)
- **Link**: [arXiv](https://arxiv.org/abs/2307.03172) | 🟡 **Intermediate** | ⏱️ 1 hour
- **Key Finding**: LLMs struggle with info in the middle of long contexts
- **Impact**: Informed RAG chunking and context placement strategies

---

## 🔍 Retrieval-Augmented Generation

### **Retrieval-Augmented Generation for Knowledge-Intensive NLP** (2020)
- **Authors**: Lewis et al. (Facebook AI)
- **Link**: [arXiv](https://arxiv.org/abs/2005.11401) | 🟢 **Beginner** | ⏱️ 1.5 hours
- **Key Contribution**: Combine retrieval with generation
- **Impact**: Foundation of RAG systems
- **Method**: Dense retrieval (DPR) + seq2seq generation

### **Sentence-BERT: Sentence Embeddings using Siamese BERT** (2019)
- **Authors**: Reimers and Gurevych
- **Link**: [arXiv](https://arxiv.org/abs/1908.10084) | 🟢 **Beginner** | ⏱️ 1 hour
- **Key Contribution**: Efficient sentence embeddings for semantic search
- **Impact**: Standard for RAG retrieval (used in vector DBs)
- **Speed**: 2000x faster than BERT cross-encoder

### **Dense Passage Retrieval for Open-Domain QA** (2020)
- **Authors**: Karpukhin et al. (Facebook AI)
- **Link**: [arXiv](https://arxiv.org/abs/2004.04906) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Dense embeddings outperform BM25 for retrieval
- **Impact**: Enabled neural search in RAG pipelines

### **Self-RAG: Learning to Retrieve, Generate, and Critique** (2023)
- **Authors**: Asai et al. (University of Washington)
- **Link**: [arXiv](https://arxiv.org/abs/2310.11511) | 🔴 **Advanced** | ⏱️ 2 hours
- **Key Contribution**: Model learns when to retrieve and self-critique
- **Innovation**: Reflection tokens for retrieval decisions

---

## 🎯 Alignment & RLHF

### **InstructGPT: Training Language Models to Follow Instructions** (2022)
- **Authors**: Ouyang et al. (OpenAI)
- **Link**: [arXiv](https://arxiv.org/abs/2203.02155) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: RLHF with human feedback
- **Impact**: Made GPT-3 → ChatGPT possible
- **Method**: SFT → Reward Model → PPO

### **Constitutional AI: Harmlessness from AI Feedback** (2022)
- **Authors**: Bai et al. (Anthropic)
- **Link**: [arXiv](https://arxiv.org/abs/2212.08073) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: AI feedback instead of human labels
- **Innovation**: Constitution-based self-critique
- **Used By**: Claude models

### **Direct Preference Optimization (DPO)** (2023)
- **Authors**: Rafailov et al. (Stanford)
- **Link**: [arXiv](https://arxiv.org/abs/2305.18290) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Simpler alternative to PPO
- **Advantage**: No reward model or RL needed
- **Impact**: Easier RLHF implementation

### **RLAIF: Scaling Reinforcement Learning from Human Feedback** (2023)
- **Authors**: Lee et al. (Google)
- **Link**: [arXiv](https://arxiv.org/abs/2309.00267) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: AI labelers match human preferences
- **Cost**: 10-100x cheaper than human labeling

---

## ⚡ Efficient Training & Inference

### **8-bit Optimizers via Block-wise Quantization** (2021)
- **Authors**: Dettmers et al.
- **Link**: [arXiv](https://arxiv.org/abs/2110.02861) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Quantize optimizer states for memory savings
- **Impact**: 2x memory reduction during training

### **ZeRO: Memory Optimizations Toward Training Trillion Parameter Models** (2019)
- **Authors**: Rajbhandari et al. (Microsoft)
- **Link**: [arXiv](https://arxiv.org/abs/1910.02054) | 🔴 **Advanced** | ⏱️ 2 hours
- **Key Contribution**: Partition optimizer states, gradients, parameters
- **Impact**: Foundation of DeepSpeed, enables 100B+ model training

### **GPT in 60 Lines of NumPy** (2023)
- **Authors**: Jay Mody
- **Link**: [Blog](https://jaykmody.com/blog/gpt-from-scratch/) | 🟢 **Beginner** | ⏱️ 2 hours
- **Type**: Tutorial, not paper
- **Value**: Best introduction to transformer implementation
- **Clarity**: Simple, educational code walkthrough

### **Efficient Memory Management for LLM Serving with PagedAttention** (2023)
- **Authors**: Kwon et al. (UC Berkeley)
- **Link**: [arXiv](https://arxiv.org/abs/2309.06180) | 🔴 **Advanced** | ⏱️ 2 hours
- **Key Contribution**: Virtual memory for KV cache
- **Impact**: Foundation of vLLM (2-4x throughput improvement)

---

## 📊 Evaluation & Benchmarking

### **Measuring Massive Multitask Language Understanding (MMLU)** (2020)
- **Authors**: Hendrycks et al. (UC Berkeley)
- **Link**: [arXiv](https://arxiv.org/abs/2009.03300) | 🟢 **Beginner** | ⏱️ 1 hour
- **Key Contribution**: 57 subject areas for comprehensive evaluation
- **Impact**: Standard benchmark for knowledge evaluation

### **HumanEval: Evaluating Large Language Models Trained on Code** (2021)
- **Authors**: Chen et al. (OpenAI)
- **Link**: [arXiv](https://arxiv.org/abs/2107.03374) | 🟢 **Beginner** | ⏱️ 1 hour
- **Key Contribution**: 164 hand-written programming problems
- **Impact**: Standard for code generation evaluation

### **TruthfulQA: Measuring How Models Mimic Human Falsehoods** (2021)
- **Authors**: Lin et al. (Oxford)
- **Link**: [arXiv](https://arxiv.org/abs/2109.07958) | 🟢 **Beginner** | ⏱️ 1 hour
- **Key Contribution**: Tests model truthfulness
- **Finding**: Larger models can be less truthful

### **Holistic Evaluation of Language Models (HELM)** (2022)
- **Authors**: Liang et al. (Stanford)
- **Link**: [arXiv](https://arxiv.org/abs/2211.09110) | 🟡 **Intermediate** | ⏱️ 2 hours
- **Key Contribution**: Multi-metric evaluation framework
- **Metrics**: Accuracy, robustness, fairness, efficiency

---

## 🖼️ Multimodal Models

### **CLIP: Learning Transferable Visual Models From Natural Language** (2021)
- **Authors**: Radford et al. (OpenAI)
- **Link**: [arXiv](https://arxiv.org/abs/2103.00020) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Joint vision-language pre-training
- **Impact**: Foundation for image generation, vision-language models

### **Flamingo: a Visual Language Model for Few-Shot Learning** (2022)
- **Authors**: Alayrac et al. (DeepMind)
- **Link**: [arXiv](https://arxiv.org/abs/2204.14198) | 🔴 **Advanced** | ⏱️ 2 hours
- **Key Contribution**: Interleaved image-text understanding
- **Architecture**: Cross-attention between frozen vision and language models

### **GPT-4 Vision System Card** (2023)
- **Authors**: OpenAI
- **Link**: [PDF](https://cdn.openai.com/papers/GPTV_System_Card.pdf) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Type**: System card, not research paper
- **Value**: Production multimodal deployment insights
- **Safety**: Refusal behavior, harmful content mitigation

---

## 🛡️ Safety & Robustness

### **Red Teaming Language Models to Reduce Harms** (2022)
- **Authors**: Ganguli et al. (Anthropic)
- **Link**: [arXiv](https://arxiv.org/abs/2209.07858) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Systematic adversarial testing
- **Method**: Red team attacks → model improvements

### **Universal and Transferable Adversarial Attacks on Aligned LLMs** (2023)
- **Authors**: Zou et al. (CMU)
- **Link**: [arXiv](https://arxiv.org/abs/2307.15043) | 🔴 **Advanced** | ⏱️ 2 hours
- **Key Finding**: Jailbreaks transfer across models
- **Impact**: Highlighted alignment fragility

### **The Foundation Model Transparency Index** (2023)
- **Authors**: Bommasani et al. (Stanford)
- **Link**: [arXiv](https://arxiv.org/abs/2310.12941) | 🟡 **Intermediate** | ⏱️ 1.5 hours
- **Key Contribution**: Framework for model transparency
- **Finding**: Most foundation models lack transparency

---

## 📚 Reading Lists by Role

### **For Beginners (Start Here)**
1. Attention Is All You Need
2. BERT
3. GPT-2
4. GPT-3
5. LLaMA
6. Chain-of-Thought Prompting
7. LoRA
8. RAG
9. MMLU
10. HumanEval

⏱️ **Total**: ~15 hours | **Goal**: Understand foundations

---

### **For ML Engineers → LLM Engineers**
1. All beginner papers above
2. LLaMA 2 (RLHF process)
3. QLoRA (efficient fine-tuning)
4. Mistral 7B (efficient architecture)
5. InstructGPT (RLHF)
6. DPO (simpler alignment)
7. ReAct (agents)
8. Self-RAG (advanced RAG)
9. Flash Attention (efficiency)
10. vLLM paper (serving)

⏱️ **Total**: ~35 hours | **Goal**: Production deployment skills

---

### **For Researchers**
1. All ML Engineer papers above
2. Chinchilla (scaling laws)
3. Mixtral (MoE)
4. Constitutional AI
5. Tree of Thoughts
6. HELM (comprehensive eval)
7. ZeRO (distributed training)
8. Flamingo (multimodal)
9. Red Teaming
10. Adversarial Attacks

⏱️ **Total**: ~55 hours | **Goal**: Research frontier

---

### **For Application Developers**
1. Attention Is All You Need
2. GPT-3
3. Chain-of-Thought
4. ReAct
5. RAG
6. Sentence-BERT
7. Lost in the Middle
8. LoRA
9. DPO
10. LLaMA 2

⏱️ **Total**: ~20 hours | **Goal**: Build production apps

---

## 🔄 Paper Reading Strategy

### **Efficient Reading Method**

1. **First Pass (15 min)**:
   - Read abstract, introduction, conclusion
   - Look at figures and tables
   - Decide if worth deeper read

2. **Second Pass (1-2 hours)**:
   - Read entire paper
   - Take notes on key contributions
   - Understand methodology

3. **Third Pass (2-4 hours)** _(Optional for critical papers)_:
   - Replicate key results
   - Compare with related work
   - Critically analyze claims

### **Study Groups**
- Join paper reading groups: [Papers We Love](https://paperswelove.org/)
- LLM paper club on Discord communities
- Twitter threads by researchers (#LLMpapers)

---

## 📖 Additional Resources

### **Paper Repositories**
- [Papers with Code - NLP](https://paperswithcode.com/area/natural-language-processing) - Papers + implementations
- [Hugging Face Papers](https://huggingface.co/papers) - Daily ML papers
- [Connected Papers](https://www.connectedpapers.com/) - Visual paper exploration

### **Research Blogs**
- [OpenAI Research](https://openai.com/research)
- [Anthropic Research](https://www.anthropic.com/research)
- [Google AI Blog](https://ai.googleblog.com/)
- [Meta AI Research](https://ai.meta.com/research/)
- [Hugging Face Blog](https://huggingface.co/blog)

### **Weekly Digests**
- [Import AI](https://jack-clark.net/) - Jack Clark's weekly AI newsletter
- [The Batch](https://www.deeplearning.ai/the-batch/) - DeepLearning.AI weekly
- [Alpha Signal](https://alphasignal.ai/) - ML research papers

---

## 🎯 Quick Selection Guide

| Your Goal | Start With |
|-----------|------------|
| Understand basics | Attention Is All You Need → BERT → GPT-3 |
| Build chatbots | Chain-of-Thought → ReAct → InstructGPT |
| Implement RAG | RAG paper → Sentence-BERT → Self-RAG |
| Fine-tune models | LoRA → QLoRA → DPO |
| Production deployment | LLaMA 2 → Flash Attention → vLLM |
| Research | Chinchilla → Mixtral → Constitutional AI |

---

## 📅 Stay Updated

- **arXiv.org** - Check daily for new papers
- **Twitter/X** - Follow @_akhaliq, @omarsar0, @hardmaru
- **Reddit** - r/MachineLearning daily papers thread
- **Hugging Face** - Daily papers section

---

**Last Updated:** October 2025

**Note**: Focus on understanding concepts over memorizing details. Implementation beats passive reading!