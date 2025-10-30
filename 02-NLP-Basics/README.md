# 📝 NLP Basics

Core NLP concepts: Tokenization, Embeddings, Transformers.

---

## 🔤 Tokenization

### Hugging Face Tokenizers
- **URL:** https://github.com/huggingface/tokenizers
- **Type:** Python Library
- **License:** Apache 2.0
- **Note:** Fast tokenizers for BPE, WordPiece, Unigram algorithms.

### Tokenizers Documentation
- **URL:** https://huggingface.co/docs/tokenizers/
- **Type:** Documentation
- **Note:** Official docs for tokenization methods and usage.

### SentencePiece
- **URL:** https://github.com/google/sentencepiece
- **Type:** Tokenizer
- **Maintainer:** Google
- **License:** Apache 2.0
- **Note:** Unsupervised tokenizer (used in LLaMA, T5, ALBERT).

### Let's Build the GPT Tokenizer
- **URL:** https://www.youtube.com/watch?v=zduSFxRajkE
- **Type:** Video (YouTube)
- **Author:** Andrej Karpathy
- **Note:** Building BPE tokenizer from scratch with code.

### tiktoken
- **URL:** https://github.com/openai/tiktoken
- **Type:** Tokenizer
- **Maintainer:** OpenAI
- **License:** MIT
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
- **URL:** https://github.com/tensorflow/tensor2tensor
- **Type:** Framework
- **Maintainer:** Google
- **License:** Apache 2.0
- **Note:** Original transformer implementation and extensions.

### x-transformers
- **URL:** https://github.com/lucidrains/x-transformers
- **Type:** Library
- **License:** MIT
- **Note:** Concise transformer variants in PyTorch.
