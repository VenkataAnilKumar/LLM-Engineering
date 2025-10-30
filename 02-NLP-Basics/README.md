# 📝 NLP Basics

Core NLP concepts: Tokenization, Embeddings, Transformers.

## 📊 Legend

- 🟢 **Beginner** - No prerequisites required
- 🟡 **Intermediate** - Basic NLP knowledge recommended
- 🔴 **Advanced** - Strong NLP foundation required
- ⏱️ **Time** - Estimated learning time
- 📅 **Updated** - Last verified date
- 🔧 **Hands-on** - Includes practical exercises
- ⭐ **Popular** - Widely used in industry

---

## 📑 Table of Contents

1. [🔤 Tokenization](#-tokenization)
2. [🔢 Word Embeddings](#-word-embeddings)
3. [🏗️ Transformer Architecture](#️-transformer-architecture)
4. [🎯 Attention Mechanisms](#-attention-mechanisms)
5. [📄 Foundational Papers](#-foundational-papers)
6. [🔍 Position Encodings](#-position-encodings)
7. [📚 Learning Resources](#-learning-resources)
8. [🛠️ Implementation Resources](#️-implementation-resources)
9. [🔀 Tokenizer Comparison](#-tokenizer-comparison)

---

## 🔤 Tokenization

### Hugging Face Tokenizers
- 🟡 Intermediate | ⏱️ 5 hours | 📅 Oct 2025 | 🔧 Hands-on | ⭐ Popular
- **URL:** https://github.com/huggingface/tokenizers
- **Type:** Python Library
- **License:** Apache 2.0
- **GitHub Stars:** 9k+
- **Languages:** Python, Rust, Node.js
- **Note:** Fast tokenizers for BPE, WordPiece, Unigram algorithms.

### Tokenizers Documentation
- 🟢 Beginner | ⏱️ 3 hours | 📅 Oct 2025
- **URL:** https://huggingface.co/docs/tokenizers/
- **Type:** Documentation
- **Note:** Official docs for tokenization methods and usage.

### SentencePiece
- 🟡 Intermediate | ⏱️ 4 hours | 📅 Oct 2025 | 🔧 Hands-on | ⭐ Popular
- **URL:** https://github.com/google/sentencepiece
- **Type:** Tokenizer
- **Maintainer:** Google
- **License:** Apache 2.0
- **GitHub Stars:** 10k+
- **Used By:** LLaMA, T5, ALBERT, XLNet
- **Note:** Unsupervised tokenizer (BPE, Unigram).

### Let's Build the GPT Tokenizer
- 🟡 Intermediate | ⏱️ 2 hours | 📅 Oct 2025 | 🔧 Hands-on
- **URL:** https://www.youtube.com/watch?v=zduSFxRajkE
- **Type:** Video (YouTube)
- **Author:** Andrej Karpathy
- **Prerequisites:** Python programming
- **Note:** Building BPE tokenizer from scratch with code.

### tiktoken
- 🟡 Intermediate | ⏱️ 2 hours | 📅 Oct 2025 | 🔧 Hands-on
- **URL:** https://github.com/openai/tiktoken
- **Type:** Tokenizer
- **Maintainer:** OpenAI
- **License:** MIT
- **GitHub Stars:** 12k+
- **Used By:** GPT-3.5, GPT-4
- **Note:** Fast BPE tokenizer for OpenAI models.

---

## 🔢 Word Embeddings

### Word2Vec Paper
- **URL:** https://arxiv.org/abs/1301.3781
- **Title:** Efficient Estimation of Word Representations in Vector Space
- **Authors:** Mikolov et al. (Google)
- **Year:** 2013
- **Note:** Original Word2Vec paper introducing CBOW and Skip-gram.

### GloVe: Global Vectors
- **URL:** https://nlp.stanford.edu/projects/glove/
- **Type:** Project Page + Pre-trained Embeddings
- **Institution:** Stanford NLP
- **Note:** Pre-trained word vectors and paper.

### FastText
- **URL:** https://github.com/facebookresearch/fastText
- **Type:** Library + Pre-trained Models
- **Maintainer:** Meta AI
- **License:** MIT
- **Note:** Word embeddings with subword information.

### The Illustrated Word2vec
- **URL:** https://jalammar.github.io/illustrated-word2vec/
- **Type:** Article
- **Author:** Jay Alammar
- **Note:** Visual explanation of Word2Vec concepts.

---

## 🏗️ Transformer Architecture

### Attention Is All You Need
- **URL:** https://arxiv.org/abs/1706.03762
- **Title:** Attention Is All You Need
- **Authors:** Vaswani et al. (Google)
- **Year:** 2017
- **Note:** Original transformer architecture paper.

### The Illustrated Transformer
- **URL:** https://jalammar.github.io/illustrated-transformer/
- **Type:** Article
- **Author:** Jay Alammar
- **Note:** Visual walkthrough of transformer architecture.

### The Annotated Transformer
- **URL:** http://nlp.seas.harvard.edu/annotated-transformer/
- **Type:** Article + Code
- **Institution:** Harvard NLP
- **Note:** Line-by-line PyTorch implementation with annotations.

### Transformers from Scratch
- **URL:** https://peterbloem.nl/blog/transformers
- **Type:** Article + Code
- **Author:** Peter Bloem
- **Note:** Minimal transformer implementation with explanations.

### nanoGPT
- **URL:** https://github.com/karpathy/nanoGPT
- **Type:** Code Repository
- **Author:** Andrej Karpathy
- **License:** MIT
- **Note:** Minimal GPT implementation for education (~300 lines).

---

## 🎯 Attention Mechanisms

### Attention? Attention!
- **URL:** https://lilianweng.github.io/posts/2018-06-24-attention/
- **Type:** Blog Post
- **Author:** Lilian Weng
- **Note:** Comprehensive attention mechanism overview.

### Visualizing Attention
- **URL:** https://poloclub.github.io/transformer-explainer/
- **Type:** Interactive Tool
- **Note:** Interactive visualization of transformer attention.

### Self-Attention Visualization
- **URL:** https://github.com/jessevig/bertviz
- **Type:** Tool
- **License:** Apache 2.0
- **Note:** Visualize attention in BERT, GPT-2, and other models.

---

## 📄 Foundational Papers

### BERT: Pre-training of Deep Bidirectional Transformers
- **URL:** https://arxiv.org/abs/1810.04805
- **Authors:** Devlin et al. (Google)
- **Year:** 2018
- **Note:** Bidirectional encoder using masked language modeling.

### GPT: Improving Language Understanding by Generative Pre-Training
- **URL:** https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf
- **Authors:** Radford et al. (OpenAI)
- **Year:** 2018
- **Note:** Original GPT paper demonstrating pre-training + fine-tuning.

### GPT-2: Language Models are Unsupervised Multitask Learners
- **URL:** https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf
- **Authors:** Radford et al. (OpenAI)
- **Year:** 2019
- **Note:** Scaled GPT showing zero-shot task performance.

### T5: Exploring the Limits of Transfer Learning
- **URL:** https://arxiv.org/abs/1910.10683
- **Authors:** Raffel et al. (Google)
- **Year:** 2019
- **Note:** Encoder-decoder model with text-to-text framework.

### RoBERTa: A Robustly Optimized BERT Pretraining Approach
- **URL:** https://arxiv.org/abs/1907.11692
- **Authors:** Liu et al. (Meta AI)
- **Year:** 2019
- **Note:** Improved BERT training methodology.

---

## 🔍 Position Encodings

### Rotary Position Embedding (RoPE)
- **URL:** https://arxiv.org/abs/2104.09864
- **Title:** RoFormer: Enhanced Transformer with Rotary Position Embedding
- **Authors:** Su et al.
- **Year:** 2021
- **Note:** Rotary position embeddings (used in LLaMA, GPT-NeoX).

### ALiBi: Attention with Linear Biases
- **URL:** https://arxiv.org/abs/2108.12409
- **Title:** Train Short, Test Long
- **Authors:** Press et al.
- **Year:** 2021
- **Note:** Position encoding for length extrapolation (used in BLOOM).

---

## 📚 Learning Resources

### Stanford CS224N: NLP with Deep Learning
- **URL:** https://web.stanford.edu/class/cs224n/
- **Type:** University Course
- **Institution:** Stanford
- **Note:** Free lecture videos covering NLP fundamentals and transformers.

### Hugging Face NLP Course
- **URL:** https://huggingface.co/learn/nlp-course/
- **Type:** Online Course
- **License:** Free
- **Note:** Comprehensive course on transformers and NLP.

### Speech and Language Processing
- **URL:** https://web.stanford.edu/~jurafsky/slp3/
- **Authors:** Jurafsky, Martin
- **Type:** Textbook (free draft)
- **Note:** NLP textbook including neural methods and transformers.

---

## 🛠️ Implementation Resources

### minGPT
- **URL:** https://github.com/karpathy/minGPT
- **Type:** Code Repository
- **Author:** Andrej Karpathy
- **License:** MIT
- **Note:** Minimal GPT implementation for education.

### Transformer Implementation
- 🟡 Intermediate | ⏱️ 10 hours | 📅 Oct 2025 | 🔧 Hands-on
- **URL:** https://github.com/tensorflow/tensor2tensor
- **Type:** Framework
- **Maintainer:** Google
- **License:** Apache 2.0
- **Note:** Original transformer implementation and extensions.

### x-transformers
- 🔴 Advanced | ⏱️ 8 hours | 📅 Oct 2025 | 🔧 Hands-on
- **URL:** https://github.com/lucidrains/x-transformers
- **Type:** Library
- **License:** MIT
- **GitHub Stars:** 4k+
- **Note:** Concise transformer variants in PyTorch.

---

## 🔀 Tokenizer Comparison

| Tokenizer | Algorithm | Speed | Use Cases | Models Using It |
|-----------|-----------|-------|-----------|-----------------|
| **tiktoken** | BPE | ⚡⚡⚡ Very Fast | OpenAI models | GPT-3.5, GPT-4 |
| **SentencePiece** | BPE/Unigram | ⚡⚡ Fast | Multilingual, subword | LLaMA, T5, ALBERT |
| **HF Tokenizers** | BPE/WordPiece/Unigram | ⚡⚡⚡ Very Fast | General purpose | BERT, GPT-2, RoBERTa |
| **WordPiece** | WordPiece | ⚡⚡ Fast | BERT-style models | BERT, DistilBERT |

---

## 🎓 Suggested Learning Path

**For Beginners:**
1. Tokenizers Documentation → Hugging Face NLP Course
2. The Illustrated Transformer → The Annotated Transformer
3. nanoGPT code → Build your own tokenizer

**For Intermediate Learners:**
1. Attention Is All You Need paper → CS224N lectures
2. Karpathy's tokenizer video → minGPT implementation
3. BERT & GPT papers → Position encoding papers

**For Advanced Researchers:**
1. All foundational papers → RoPE & ALiBi papers
2. x-transformers library → Speech and Language Processing book
3. Implement transformer variants

---

**Key Papers to Read:**
1. Attention Is All You Need (2017) - Original transformer
2. BERT (2018) - Bidirectional pre-training
3. GPT-2 (2019) - Scaling laws emergence
4. T5 (2019) - Text-to-text framework
5. RoPE (2021) - Modern position encoding

---

**Last Updated:** October 2025
