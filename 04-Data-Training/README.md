# 🗃️ Data & Training

Open datasets, data preparation, training frameworks.

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
- **URL:** https://arxiv.org/abs/2203.15556
- **Title:** Training Compute-Optimal Large Language Models
- **Authors:** Hoffmann et al. (DeepMind)
- **Note:** Optimal data/model size trade-offs.
