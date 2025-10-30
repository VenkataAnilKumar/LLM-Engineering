# 🗃️ Data & Training

Open datasets, data preparation, training frameworks.

## 📊 Legend

- 🟢 **Beginner** - Ready to use, minimal setup
- 🟡 **Intermediate** - Requires processing/configuration
- 🔴 **Advanced** - Complex setup, large-scale
- 💾 **Size** - Dataset size
- ⏱️ **Processing Time** - Estimated time to prepare
- 📅 **Updated** - Last verified date
- 🔓 **License** - Usage terms
- 🌍 **Languages** - Language support

---

## 📑 Table of Contents

1. [📚 Pre-training Datasets](#-pre-training-datasets)
2. [🎯 Instruction & Fine-tuning Datasets](#-instruction--fine-tuning-datasets)
3. [💻 Code Datasets](#-code-datasets)
4. [🧪 Evaluation Datasets](#-evaluation-datasets)
5. [🛠️ Data Processing Tools](#️-data-processing-tools)
6. [🚀 Training Frameworks](#-training-frameworks)
7. [🔧 Data Cleaning & Quality](#-data-cleaning--quality)
8. [📊 Dataset Utilities](#-dataset-utilities)
9. [📚 Learning Resources](#-learning-resources)
10. [🔀 Dataset Comparison](#-dataset-comparison)

---

## 📚 Pre-training Datasets

### The Pile
- **URL:** https://pile.eleuther.ai/
- **Type:** Dataset
- **Size:** 825 GB
- **Maintainer:** EleutherAI
- **License:** Various (mostly permissive)
- **Note:** 22 diverse high-quality text sources.

### C4: Colossal Clean Crawled Corpus
- **URL:** https://www.tensorflow.org/datasets/catalog/c4
- **Type:** Dataset
- **Size:** 750+ GB
- **Source:** Common Crawl
- **Note:** Cleaned web text used in T5, GPT-Neo.

### RedPajama
- **URL:** https://github.com/togethercomputer/RedPajama-Data
- **Type:** Dataset
- **Size:** 1.2 trillion tokens
- **License:** Various open licenses
- **Note:** Open reproduction of LLaMA training data.

### OSCAR: Open Super-large Crawled Aggregated coRpus
- **URL:** https://huggingface.co/datasets/oscar
- **Type:** Dataset
- **Source:** Common Crawl
- **Note:** Multilingual web corpus (160+ languages).

### Wikipedia Dumps
- **URL:** https://dumps.wikimedia.org/
- **Type:** Dataset
- **License:** CC BY-SA
- **Note:** Full Wikipedia dumps in all languages.

### Books3
- **URL:** https://huggingface.co/datasets/the_pile_books3
- **Type:** Dataset (part of The Pile)
- **Note:** Book corpus for language modeling.

### Gutenberg
- **URL:** https://www.gutenberg.org/
- **Type:** Dataset
- **License:** Public Domain
- **Note:** 70,000+ free public domain books.

---

## 🎯 Instruction & Fine-tuning Datasets

### Alpaca Dataset
- **URL:** https://github.com/tatsu-lab/stanford_alpaca
- **Type:** Dataset
- **Size:** 52K instructions
- **Institution:** Stanford
- **License:** CC BY-NC 4.0
- **Note:** Self-instruct generated instruction-following data.

### Dolly 2.0
- **URL:** https://huggingface.co/datasets/databricks/databricks-dolly-15k
- **Type:** Dataset
- **Size:** 15K instructions
- **Maintainer:** Databricks
- **License:** CC BY-SA 3.0
- **Note:** Human-generated instruction-response pairs.

### OpenAssistant Conversations
- **URL:** https://huggingface.co/datasets/OpenAssistant/oasst1
- **Type:** Dataset
- **Size:** 161K messages
- **License:** Apache 2.0
- **Note:** Multi-turn conversational data.

### FLAN Collection
- **URL:** https://github.com/google-research/FLAN
- **Type:** Dataset Collection
- **Maintainer:** Google
- **Note:** Instruction tuning datasets from multiple sources.

### ShareGPT
- **URL:** https://huggingface.co/datasets/anon8231489123/ShareGPT_Vicuna_unfiltered
- **Type:** Dataset
- **License:** Various
- **Note:** Shared ChatGPT conversations.

### Orca Dataset (Explanation Tuning)
- **URL:** https://arxiv.org/abs/2306.02707
- **Type:** Paper + Methodology
- **Authors:** Microsoft
- **Year:** 2023
- **Note:** Learning from step-by-step explanations.

---

## 💻 Code Datasets

### The Stack
- **URL:** https://huggingface.co/datasets/bigcode/the-stack
- **Type:** Dataset
- **Size:** 3.1 TB
- **License:** Multiple open licenses
- **Note:** Source code in 30+ programming languages.

### CodeParrot
- **URL:** https://huggingface.co/datasets/codeparrot/github-code
- **Type:** Dataset
- **License:** Various open licenses
- **Note:** GitHub code filtered for quality.

### Human Eval
- **URL:** https://github.com/openai/human-eval
- **Type:** Benchmark Dataset
- **Maintainer:** OpenAI
- **Note:** 164 programming problems for evaluation.

---

## 🧪 Evaluation Datasets

### MMLU Dataset
- **URL:** https://github.com/hendrycks/test
- **Type:** Benchmark
- **Size:** 15,908 questions across 57 tasks
- **Note:** Multitask language understanding evaluation.

### TruthfulQA
- **URL:** https://github.com/sylinrl/TruthfulQA
- **Type:** Benchmark
- **Size:** 817 questions
- **Note:** Tests factual accuracy and truthfulness.

### GSM8K: Grade School Math
- **URL:** https://github.com/openai/grade-school-math
- **Type:** Benchmark
- **Size:** 8,500 problems
- **Maintainer:** OpenAI
- **Note:** Math word problems requiring multi-step reasoning.

---

## 🛠️ Data Processing Tools

### datasets (Hugging Face)
- **URL:** https://github.com/huggingface/datasets
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Loading and processing datasets with memory mapping.

### cleaned-pile
- **URL:** https://github.com/EleutherAI/the-pile
- **Type:** Processing Scripts
- **Maintainer:** EleutherAI
- **Note:** Scripts for processing The Pile dataset.

### cc_net
- **URL:** https://github.com/facebookresearch/cc_net
- **Type:** Tool
- **Maintainer:** Meta Research
- **License:** MIT
- **Note:** Tools for processing Common Crawl.

### datatrove
- **URL:** https://github.com/huggingface/datatrove
- **Type:** Library
- **Maintainer:** Hugging Face
- **License:** Apache 2.0
- **Note:** Large-scale data processing pipeline.

---

## 🚀 Training Frameworks

### DeepSpeed
- **URL:** https://github.com/microsoft/DeepSpeed
- **Type:** Training Library
- **Maintainer:** Microsoft
- **License:** Apache 2.0
- **Note:** ZeRO optimization for distributed training.

### Megatron-LM
- **URL:** https://github.com/NVIDIA/Megatron-LM
- **Type:** Training Framework
- **Maintainer:** NVIDIA
- **License:** BSD 3-Clause
- **Note:** Large-scale transformer training with model parallelism.

### Megatron-DeepSpeed
- **URL:** https://github.com/microsoft/Megatron-DeepSpeed
- **Type:** Training Framework
- **Maintainer:** Microsoft
- **License:** Apache 2.0
- **Note:** Combines Megatron and DeepSpeed optimizations.

### Accelerate
- **URL:** https://github.com/huggingface/accelerate
- **Type:** Library
- **Maintainer:** Hugging Face
- **License:** Apache 2.0
- **Note:** Simplified distributed training for PyTorch.

### PyTorch FSDP
- **URL:** https://pytorch.org/docs/stable/fsdp.html
- **Type:** PyTorch Module
- **License:** BSD
- **Note:** Fully Sharded Data Parallel for distributed training.

### Composer
- **URL:** https://github.com/mosaicml/composer
- **Type:** Training Library
- **Maintainer:** MosaicML
- **License:** Apache 2.0
- **Note:** Speed up training with algorithmic improvements.

---

## 🔧 Data Cleaning & Quality

### cc_net (Common Crawl Processing)
- **URL:** https://github.com/facebookresearch/cc_net
- **Type:** Tool
- **License:** MIT
- **Note:** Cleaning and filtering Common Crawl data.

### deduplicate-text-datasets
- **URL:** https://github.com/google-research/deduplicate-text-datasets
- **Type:** Tool
- **Maintainer:** Google Research
- **Note:** Deduplication for text datasets.

### DEDUP: Near-Duplicate Text Removal
- **URL:** https://github.com/ChenghaoMou/text-dedup
- **Type:** Tool
- **License:** MIT
- **Note:** Efficient near-duplicate detection.

---

## 📊 Dataset Utilities

### promptsource
- **URL:** https://github.com/bigscience-workshop/promptsource
- **Type:** Tool
- **License:** Apache 2.0
- **Note:** Creating and sharing prompts for datasets.

### FairSeq
- **URL:** https://github.com/facebookresearch/fairseq
- **Type:** Framework
- **Maintainer:** Meta AI
- **License:** MIT
- **Note:** Sequence modeling toolkit with data utilities.

---

## 📚 Learning Resources

### Practical Data Preprocessing for LLMs
- **URL:** https://huggingface.co/blog/lm-datasets
- **Type:** Blog Post
- **Note:** Best practices for dataset preparation.

### Scaling Laws Paper
- **URL:** https://arxiv.org/abs/2001.08361
- **Title:** Scaling Laws for Neural Language Models
- **Authors:** Kaplan et al. (OpenAI)
- **Note:** Relationship between data size, model size, and performance.

### Chinchilla Paper
- 🔴 Advanced | ⏱️ 3 hours | 📅 2022
- **URL:** https://arxiv.org/abs/2203.15556
- **Title:** Training Compute-Optimal Large Language Models
- **Authors:** Hoffmann et al. (DeepMind)
- **Note:** Optimal data/model size trade-offs.

---

## 🔀 Dataset Comparison

### Pre-training Datasets

| Dataset | Size | Languages | Quality | License | Best For |
|---------|------|-----------|---------|---------|----------|
| **The Pile** | 825 GB | EN | ⭐⭐⭐⭐⭐ Excellent | Mixed | General pre-training |
| **C4** | 750+ GB | EN | ⭐⭐⭐⭐ High | ODC-BY | Clean web text |
| **RedPajama** | 1.2T tokens | EN | ⭐⭐⭐⭐ High | Various | LLaMA-style training |
| **OSCAR** | ~6 TB | 160+ | ⭐⭐⭐ Good | CC0 | Multilingual |
| **Wikipedia** | ~20 GB | 300+ | ⭐⭐⭐⭐⭐ Excellent | CC BY-SA | Factual knowledge |
| **mC4** | Massive | 100+ | ⭐⭐⭐⭐ High | ODC-BY | Multilingual web |

### Instruction Datasets

| Dataset | Size | Type | Quality | Use Case |
|---------|------|------|---------|----------|
| **Alpaca** | 52K | Single-turn | ⭐⭐⭐ Good | General instruction following |
| **Dolly 2.0** | 15K | Single-turn | ⭐⭐⭐⭐ High | Human-quality instructions |
| **OpenAssistant** | 161K msgs | Multi-turn | ⭐⭐⭐⭐ High | Conversational assistant |
| **ShareGPT** | Varies | Multi-turn | ⭐⭐⭐ Good | Chat-style interactions |
| **FLAN** | 1800+ tasks | Task-specific | ⭐⭐⭐⭐⭐ Excellent | Multi-task instruction tuning |
| **Orca** | Synthetic | Explanation | ⭐⭐⭐⭐ High | Reasoning and explanations |

### Code Datasets

| Dataset | Size | Languages | License | Best For |
|---------|------|-----------|---------|----------|
| **The Stack** | 6 TB | 358 | Permissive only | General code training |
| **CodeParrot** | 50 GB | 50+ | Apache 2.0 | Python-focused training |
| **StarCoder Data** | 783 GB | 86 | Various | Multi-language code |
| **GitHub Code** | Massive | 100+ | Various | Real-world code |

### Training Frameworks Comparison

| Framework | Best For | Hardware | Scale | Ease of Use |
|-----------|----------|----------|-------|-------------|
| **DeepSpeed** | Large models | Multi-GPU, Multi-node | ⭐⭐⭐⭐⭐ Massive | 🟡 Medium |
| **Megatron-LM** | Massive scale | Multi-node required | ⭐⭐⭐⭐⭐ Massive | 🔴 Complex |
| **Accelerate** | Flexibility | Any setup | ⭐⭐⭐⭐ Large | 🟢 Easy |
| **ColossalAI** | Optimization | Multi-GPU | ⭐⭐⭐⭐ Large | 🟡 Medium |
| **FSDP** | PyTorch native | Multi-GPU | ⭐⭐⭐⭐ Large | 🟡 Medium |
| **Axolotl** | Fine-tuning | Single/Multi-GPU | ⭐⭐⭐ Medium | 🟢 Easy |

---

## 🎓 Suggested Learning Path

**Phase 1: Understanding Data (Week 1-2)**
1. Read Scaling Laws paper (understand data requirements)
2. Explore The Pile (understand pre-training data composition)
3. Study Chinchilla paper (optimal data/model ratios)
4. Download and inspect small datasets (Alpaca, Dolly)

**Phase 2: Data Processing (Week 3-4)**
1. Learn Hugging Face Datasets library
2. Practice with data cleaning tools (fastText langdetect)
3. Implement deduplication (text-dedup)
4. Create custom dataset for fine-tuning

**Phase 3: Training Setup (Week 5-6)**
1. Start with Accelerate for simple distributed training
2. Experiment with DeepSpeed ZeRO stages
3. Try Axolotl for streamlined fine-tuning
4. Monitor with Weights & Biases

**Phase 4: Advanced (Week 7-8)**
1. Explore Megatron-LM for massive scale
2. Implement custom data pipelines
3. Study dataset mixing strategies
4. Benchmark different training configurations

---

## 🔑 Key Considerations

**Dataset Selection:**
- **Pre-training**: Use diverse, high-quality data (The Pile, RedPajama)
- **Fine-tuning**: Smaller, domain-specific datasets (1K-50K examples)
- **Instruction tuning**: Mix multiple instruction datasets (FLAN approach)
- **Code**: Use filtered datasets (The Stack v2 with opt-out respected)

**Data Quality over Quantity:**
- Chinchilla scaling laws: ~20 tokens per parameter optimal
- Quality filtering crucial (deduplication, language detection, toxicity)
- Human-curated data (Dolly) often better than synthetic (but smaller)

**Training Framework Selection:**
- **Single GPU**: Standard PyTorch/HF Transformers
- **Multi-GPU (same node)**: Accelerate or DeepSpeed ZeRO-2
- **Multi-node**: DeepSpeed ZeRO-3 or Megatron-LM
- **Consumer GPUs**: Axolotl with QLoRA for efficiency

**Licensing:**
- Always check dataset licenses (commercial use, redistribution)
- The Pile: Mixed licenses, check individual sources
- The Stack v2: Only permissive licenses
- ShareGPT: Unclear provenance, use with caution

---

**Last Updated:** October 2025
