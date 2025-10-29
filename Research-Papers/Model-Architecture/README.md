# 📄 Research Papers - Model Architecture

A curated collection of essential research papers on LLM architectures, from foundational transformers to cutting-edge designs.

---

## 🎯 Overview

This section covers papers on:
- Transformer architecture fundamentals
- Encoder-only models (BERT-style)
- Decoder-only models (GPT-style)
- Encoder-decoder models (T5-style)
- Mixture of Experts (MoE)
- Efficient architectures
- Alternative architectures

---

## 📚 Foundational Papers (Must Read)

### 🌟 **Attention Is All You Need** (2017)
**Authors**: Vaswani et al. (Google)  
**Link**: https://arxiv.org/abs/1706.03762  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Introduced transformer architecture
- Self-attention mechanism
- Positional encoding
- Multi-head attention

**Why Read**: Foundation of all modern LLMs. Essential for understanding anything that follows.

**Summary**: Revolutionized NLP by replacing recurrence with attention mechanisms, enabling parallel processing and better long-range dependencies.

---

### 🌟 **BERT: Pre-training of Deep Bidirectional Transformers** (2018)
**Authors**: Devlin et al. (Google)  
**Link**: https://arxiv.org/abs/1810.04805  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Bidirectional training
- Masked Language Modeling (MLM)
- Next Sentence Prediction (NSP)
- Transfer learning for NLP

**Why Read**: Showed power of pre-training and fine-tuning paradigm.

**Follow-up Work**:
- RoBERTa (improved BERT)
- ALBERT (lighter BERT)
- DeBERTa (enhanced BERT)

---

### 🌟 **Language Models are Unsupervised Multitask Learners (GPT-2)** (2019)
**Authors**: Radford et al. (OpenAI)  
**Link**: https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Demonstrated zero-shot learning
- Scaled decoder-only models
- Showed generative capabilities
- 1.5B parameters

**Why Read**: Bridge between small and large language models. Showed emergent capabilities.

---

### 🌟 **Language Models are Few-Shot Learners (GPT-3)** (2020)
**Authors**: Brown et al. (OpenAI)  
**Link**: https://arxiv.org/abs/2005.14165  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- 175B parameters
- In-context learning
- Few-shot prompting
- Scaling laws validation

**Why Read**: Defined the modern LLM era. Showed that scale unlocks new capabilities.

**Key Insights**:
- Emergent abilities appear at scale
- Few-shot > fine-tuning for many tasks
- Compute-optimal training matters

---

## 🔄 Encoder-Only Architectures

### **RoBERTa: A Robustly Optimized BERT Pretraining Approach** (2019)
**Link**: https://arxiv.org/abs/1907.11692  
**Impact**: ⭐⭐⭐⭐

**Improvements over BERT**:
- Remove NSP task
- Longer training
- Larger batches
- More data
- Dynamic masking

---

### **ALBERT: A Lite BERT** (2019)
**Link**: https://arxiv.org/abs/1909.11942  
**Impact**: ⭐⭐⭐

**Key Innovations**:
- Parameter sharing across layers
- Factorized embedding
- Inter-sentence coherence
- Fewer parameters, better performance

---

### **DeBERTa: Decoding-enhanced BERT with Disentangled Attention** (2020)
**Link**: https://arxiv.org/abs/2006.03654  
**Impact**: ⭐⭐⭐⭐

**Key Features**:
- Disentangled attention (content + position)
- Enhanced mask decoder
- State-of-the-art on GLUE/SuperGLUE

---

## 🎮 Decoder-Only Architectures

### **PaLM: Scaling Language Modeling with Pathways** (2022)
**Link**: https://arxiv.org/abs/2204.02311  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- 540B parameters
- Pathways distributed system
- Breakthrough on reasoning tasks
- Chain-of-thought capabilities

**Highlights**:
- Few-shot learning excellence
- Multilingual capabilities
- Code understanding

---

### **LLaMA: Open and Efficient Foundation Language Models** (2023)
**Link**: https://arxiv.org/abs/2302.13971  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Open weights (7B-65B)
- Trained on public data
- Compute-efficient
- Enabled open-source LLM research

**Why Important**: Democratized LLM research. Spawned entire ecosystem (Alpaca, Vicuna, etc.)

---

### **LLaMA 2: Open Foundation and Fine-Tuned Chat Models** (2023)
**Link**: https://arxiv.org/abs/2307.09288  
**Impact**: ⭐⭐⭐⭐⭐

**Improvements**:
- Commercially usable
- Better safety alignment
- Longer context (4096 tokens)
- 7B, 13B, 70B sizes

---

### **Mistral 7B** (2023)
**Link**: https://arxiv.org/abs/2310.06825  
**Impact**: ⭐⭐⭐⭐

**Key Features**:
- Grouped-query attention (GQA)
- Sliding window attention
- Best-in-class 7B model
- Efficient inference

---

## 🔀 Encoder-Decoder Architectures

### **Exploring the Limits of Transfer Learning with T5** (2019)
**Link**: https://arxiv.org/abs/1910.10683  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Text-to-text framework
- Unified architecture
- Systematic study of pre-training
- C4 dataset introduction

**Why Read**: Comprehensive study of what works in pre-training.

---

### **BART: Denoising Sequence-to-Sequence Pre-training** (2019)
**Link**: https://arxiv.org/abs/1910.13461  
**Impact**: ⭐⭐⭐⭐

**Key Features**:
- Combines BERT and GPT approaches
- Denoising autoencoder
- Strong on summarization
- Flexible corruption schemes

---

### **Flan-T5: Scaling Instruction-Finetuned Language Models** (2022)
**Link**: https://arxiv.org/abs/2210.11416  
**Impact**: ⭐⭐⭐⭐

**Key Contributions**:
- Instruction fine-tuning at scale
- 1800+ tasks
- Strong zero-shot performance
- Open weights

---

## 🔧 Mixture of Experts (MoE)

### **Switch Transformers: Scaling to Trillion Parameter Models** (2021)
**Link**: https://arxiv.org/abs/2101.03961  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Simplified MoE routing
- 1.6T parameters
- Sparse activation
- 7x faster training

**Key Insights**:
- Larger models, similar inference cost
- Expert specialization emerges
- Load balancing critical

---

### **GLaM: Efficient Scaling of Language Models with MoE** (2021)
**Link**: https://arxiv.org/abs/2112.06905  
**Impact**: ⭐⭐⭐⭐

**Key Features**:
- 1.2T parameters
- Energy efficient
- Better than GPT-3 with 1/3 compute
- Sparse gating

---

### **Mixtral 8x7B** (2024)
**Link**: https://arxiv.org/abs/2401.04088  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Open-source MoE
- 8 experts, 2 active per token
- 46.7B total, 12.9B active
- State-of-the-art open model

**Why Important**: Made MoE accessible to open-source community.

---

## ⚡ Efficient Architectures

### **Longformer: The Long-Document Transformer** (2020)
**Link**: https://arxiv.org/abs/2004.05150  
**Impact**: ⭐⭐⭐⭐

**Key Features**:
- Sparse attention patterns
- 4096+ token context
- Linear scaling
- Local + global attention

---

### **Linformer: Self-Attention with Linear Complexity** (2020)
**Link**: https://arxiv.org/abs/2006.04768  
**Impact**: ⭐⭐⭐

**Key Contribution**:
- O(n) complexity instead of O(n²)
- Low-rank approximation
- Efficient long sequences

---

### **Flash Attention: Fast and Memory-Efficient Exact Attention** (2022)
**Link**: https://arxiv.org/abs/2205.14135  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- 2-4x faster training
- Exact attention (not approximate)
- Better memory efficiency
- Widely adopted

---

### **Flash Attention-2** (2023)
**Link**: https://arxiv.org/abs/2307.08691  
**Impact**: ⭐⭐⭐⭐

**Improvements**:
- 2x faster than Flash Attention
- Better parallelism
- Work partitioning optimization

---

## 🆕 Alternative Architectures

### **RWKV: Reinventing RNNs for the Transformer Era** (2023)
**Link**: https://arxiv.org/abs/2305.13048  
**Impact**: ⭐⭐⭐

**Key Features**:
- RNN-Transformer hybrid
- Linear attention
- Efficient inference
- Competitive performance

---

### **Mamba: Linear-Time Sequence Modeling with Selective State Spaces** (2023)
**Link**: https://arxiv.org/abs/2312.00752  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- State space model (SSM)
- Linear scaling
- Matches transformer quality
- 5x higher throughput

**Why Important**: Potential alternative to attention mechanism.

---

### **Retentive Network: A Successor to Transformer for LLMs** (2023)
**Link**: https://arxiv.org/abs/2307.08621  
**Impact**: ⭐⭐⭐

**Key Innovation**:
- Parallel training (like transformer)
- Recurrent inference (like RNN)
- O(1) complexity for inference
- Competitive performance

---

## 📊 Architectural Analysis & Theory

### **Formal Algorithms for Transformers** (2022)
**Link**: https://arxiv.org/abs/2207.09238  
**Impact**: ⭐⭐⭐⭐

**Content**:
- Mathematical formalization
- Algorithm descriptions
- Theoretical analysis
- Implementation guidance

---

### **A Mathematical Framework for Transformer Circuits** (2021)
**Link**: https://transformer-circuits.pub/2021/framework/index.html  
**Impact**: ⭐⭐⭐⭐⭐

**Key Contributions**:
- Mechanistic understanding
- Circuit analysis
- Attention head roles
- Compositional behavior

---

### **The Annotated Transformer** (Harvard NLP)
**Link**: http://nlp.seas.harvard.edu/annotated-transformer/  
**Impact**: ⭐⭐⭐⭐⭐

**Why Valuable**:
- Line-by-line code explanation
- Clear illustrations
- Practical implementation
- Educational resource

---

## 🎯 How to Read These Papers

### For Beginners
1. Start with "Attention Is All You Need"
2. Read visual guides (Jay Alammar's blog)
3. Read BERT and GPT-2 papers
4. Focus on intuitions, skip heavy math

### For Intermediate
1. Read GPT-3 and T5 papers
2. Study architectural comparisons
3. Dive into optimization papers
4. Understand trade-offs

### For Advanced
1. Read all foundational + recent papers
2. Study architectural innovations
3. Analyze theoretical frameworks
4. Compare approaches critically

---

## 📖 Reading Strategy

**First Pass** (30 min):
- Abstract
- Introduction
- Conclusion
- Figures/tables

**Second Pass** (1-2 hours):
- Methodology
- Results
- Key equations
- Take notes

**Third Pass** (3+ hours):
- Deep understanding
- Reproduce results
- Compare with related work
- Identify limitations

---

## 🔗 Additional Resources

### Paper Repositories
- **[Papers with Code](https://paperswithcode.com/)** - Papers + implementations
- **[Hugging Face Papers](https://huggingface.co/papers)** - Daily paper discussions
- **[ArXiv Sanity](http://www.arxiv-sanity.com/)** - Paper recommendations

### Visual Explanations
- **[Jay Alammar's Blog](https://jalammar.github.io/)** - Illustrated papers
- **[The Annotated Transformer](http://nlp.seas.harvard.edu/annotated-transformer/)** - Code walkthrough

### Paper Reading Groups
- **[MLAIR Reading Group](https://www.youtube.com/@mlair)**
- **[Yannic Kilcher](https://www.youtube.com/@YannicKilcher)** - Paper explanations

---

## 📅 Stay Updated

- **ArXiv** - cs.CL, cs.LG daily
- **Twitter/X** - Follow researchers
- **Conferences** - NeurIPS, ICML, ICLR, ACL, EMNLP
- **Newsletters** - Import AI, The Batch

---

<div align="center">

**[⬆ Back to Top](#-research-papers---model-architecture)** | **[➡️ Training Techniques](../Training-Techniques/)**

</div>
