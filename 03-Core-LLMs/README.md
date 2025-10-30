# 🤖 Core LLMs

Model architectures, fine-tuning methods, evaluation benchmarks.

---

## 📄 Model Architecture Papers

### GPT-3: Language Models are Few-Shot Learners
- **URL:** https://arxiv.org/abs/2005.14165
- **Authors:** Brown et al. (OpenAI)
- **Year:** 2020
- **Note:** 175B parameter model demonstrating few-shot learning.

### PaLM: Scaling Language Modeling with Pathways
- **URL:** https://arxiv.org/abs/2204.02311
- **Authors:** Chowdhery et al. (Google)
- **Year:** 2022
- **Note:** 540B parameter model with breakthrough performance.

### LLaMA: Open and Efficient Foundation Language Models
- **URL:** https://arxiv.org/abs/2302.13971
- **Authors:** Touvron et al. (Meta AI)
- **Year:** 2023
- **Note:** Efficient open models (7B-65B parameters).

### LLaMA 2: Open Foundation and Fine-Tuned Chat Models
- **URL:** https://arxiv.org/abs/2307.09288
- **Authors:** Touvron et al. (Meta AI)
- **Year:** 2023
- **Note:** Improved LLaMA with commercial license and chat variants.

### Mistral 7B
- **URL:** https://arxiv.org/abs/2310.06825
- **Authors:** Jiang et al. (Mistral AI)
- **Year:** 2023
- **Note:** 7B model with grouped-query attention and sliding window.

### Mixtral 8x7B: A Sparse Mixture of Experts Model
- **URL:** https://arxiv.org/abs/2401.04088
- **Authors:** Jiang et al. (Mistral AI)
- **Year:** 2024
- **Note:** Sparse MoE with 8 expert networks.

### Gemma: Open Models Based on Gemini Research and Technology
- **URL:** https://arxiv.org/abs/2403.08295
- **Authors:** Gemma Team (Google)
- **Year:** 2024
- **Note:** Open 2B and 7B models from Google.

### Phi-3 Technical Report
- **URL:** https://arxiv.org/abs/2404.14219
- **Authors:** Abdin et al. (Microsoft)
- **Year:** 2024
- **Note:** Small language models (3.8B) with strong performance.

---

## 🔧 Fine-Tuning Methods

### LoRA: Low-Rank Adaptation of Large Language Models
- **URL:** https://arxiv.org/abs/2106.09685
- **Authors:** Hu et al. (Microsoft)
- **Year:** 2021
- **Note:** Parameter-efficient fine-tuning via low-rank matrices.

### QLoRA: Efficient Finetuning of Quantized LLMs
- **URL:** https://arxiv.org/abs/2305.14314
- **Authors:** Dettmers et al.
- **Year:** 2023
- **Note:** 4-bit quantization + LoRA for efficient fine-tuning.

### Prefix-Tuning
- **URL:** https://arxiv.org/abs/2101.00190
- **Authors:** Li, Liang (Stanford)
- **Year:** 2021
- **Note:** Prepending trainable continuous vectors.

### P-Tuning v2
- **URL:** https://arxiv.org/abs/2110.07602
- **Authors:** Liu et al. (Tsinghua)
- **Year:** 2021
- **Note:** Deep prompt tuning across all layers.

### Adapter Layers
- **URL:** https://arxiv.org/abs/1902.00751
- **Title:** Parameter-Efficient Transfer Learning for NLP
- **Authors:** Houlsby et al. (Google)
- **Year:** 2019
- **Note:** Inserting small adapter modules between layers.

---

## 🎯 Instruction Tuning

### FLAN: Finetuned Language Models Are Zero-Shot Learners
- **URL:** https://arxiv.org/abs/2109.01652
- **Authors:** Wei et al. (Google)
- **Year:** 2021
- **Note:** Instruction tuning for zero-shot task generalization.

### Scaling Instruction-Finetuned Language Models
- **URL:** https://arxiv.org/abs/2210.11416
- **Authors:** Chung et al. (Google)
- **Year:** 2022
- **Note:** FLAN-T5, FLAN-PaLM scaling analysis.

### Self-Instruct
- **URL:** https://arxiv.org/abs/2212.10560
- **Authors:** Wang et al. (University of Washington)
- **Year:** 2022
- **Note:** Bootstrapping instruction data from language models.

### Alpaca: A Strong, Replicable Instruction-Following Model
- **URL:** https://crfm.stanford.edu/2023/03/13/alpaca.html
- **Type:** Blog Post + Model
- **Institution:** Stanford CRFM
- **Note:** LLaMA fine-tuned on 52K instructions.

---

## 🏆 Evaluation Benchmarks

### MMLU: Measuring Massive Multitask Language Understanding
- **URL:** https://arxiv.org/abs/2009.03300
- **Authors:** Hendrycks et al.
- **Year:** 2020
- **Note:** 57 tasks covering STEM, humanities, social sciences.

### HellaSwag: Can a Machine Really Finish Your Sentence?
- **URL:** https://arxiv.org/abs/1905.07830
- **Authors:** Zellers et al.
- **Year:** 2019
- **Note:** Commonsense reasoning benchmark.

### HumanEval: Evaluating Large Language Models Trained on Code
- **URL:** https://arxiv.org/abs/2107.03374
- **Authors:** Chen et al. (OpenAI)
- **Year:** 2021
- **Note:** Coding ability evaluation (164 programming problems).

### TruthfulQA: Measuring How Models Mimic Human Falsehoods
- **URL:** https://arxiv.org/abs/2109.07958
- **Authors:** Lin et al.
- **Year:** 2021
- **Note:** Tests for truthfulness and factual accuracy.

### BIG-Bench
- **URL:** https://github.com/google/BIG-bench
- **Type:** Benchmark Suite
- **Maintainer:** Google
- **Note:** 200+ diverse evaluation tasks.

### Open LLM Leaderboard
- **URL:** https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard
- **Type:** Leaderboard
- **Maintainer:** Hugging Face
- **Note:** Standardized evaluation across multiple benchmarks.

---

## 📊 Evaluation Frameworks

### lm-evaluation-harness
- **URL:** https://github.com/EleutherAI/lm-evaluation-harness
- **Type:** Evaluation Framework
- **Maintainer:** EleutherAI
- **License:** MIT
- **Note:** Unified framework for LLM evaluation.

### OpenAI Evals
- **URL:** https://github.com/openai/evals
- **Type:** Evaluation Framework
- **Maintainer:** OpenAI
- **License:** MIT
- **Note:** Framework for evaluating LLMs with custom benchmarks.

### HELM: Holistic Evaluation of Language Models
- **URL:** https://crfm.stanford.edu/helm/
- **Type:** Benchmark + Framework
- **Institution:** Stanford CRFM
- **Note:** Comprehensive evaluation across scenarios and metrics.

---

## 🔍 Model Analysis

### Scaling Laws for Neural Language Models
- **URL:** https://arxiv.org/abs/2001.08361
- **Authors:** Kaplan et al. (OpenAI)
- **Year:** 2020
- **Note:** Power laws relating model size, data, compute to performance.

### Training Compute-Optimal Large Language Models (Chinchilla)
- **URL:** https://arxiv.org/abs/2203.15556
- **Authors:** Hoffmann et al. (DeepMind)
- **Year:** 2022
- **Note:** Optimal model size vs training tokens trade-off.

### Emergent Abilities of Large Language Models
- **URL:** https://arxiv.org/abs/2206.07682
- **Authors:** Wei et al. (Google)
- **Year:** 2022
- **Note:** Capabilities emerging only at scale.

---

## 🛠️ Open Model Repositories

### Hugging Face Model Hub
- **URL:** https://huggingface.co/models
- **Type:** Model Repository
- **Note:** 500K+ open models including LLaMA, Mistral, Gemma variants.

### LLaMA Models
- **URL:** https://huggingface.co/meta-llama
- **Type:** Model Collection
- **Maintainer:** Meta AI
- **Note:** Official LLaMA and LLaMA 2 models.

### Mistral AI Models
- **URL:** https://huggingface.co/mistralai
- **Type:** Model Collection
- **Maintainer:** Mistral AI
- **Note:** Mistral 7B, Mixtral 8x7B, and variants.

### EleutherAI Models
- **URL:** https://huggingface.co/EleutherAI
- **Type:** Model Collection
- **Maintainer:** EleutherAI
- **Note:** GPT-Neo, GPT-J, Pythia model families.

---

## 📚 Learning Resources

### State of GPT
- **URL:** https://www.youtube.com/watch?v=bZQun8Y4L2A
- **Type:** Video (YouTube)
- **Author:** Andrej Karpathy
- **Note:** Overview of GPT training, fine-tuning, and usage (1 hour).

### Transformer Models Survey
- **URL:** https://arxiv.org/abs/2106.04554
- **Title:** A Survey of Transformers
- **Authors:** Lin et al.
- **Year:** 2021
- **Note:** Comprehensive survey of transformer variants.

### Large Language Models: A Survey
- **URL:** https://arxiv.org/abs/2303.18223
- **Authors:** Zhao et al.
- **Year:** 2023
- **Note:** Extensive survey of LLM developments and techniques.
