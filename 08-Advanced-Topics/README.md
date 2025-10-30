# 🔬 Advanced Topics

RLHF, Alignment, Multimodal, Safety, Emerging research.

## 📊 Legend

- 🟢 **Accessible** - Practical implementations available
- 🟡 **Research** - Emerging techniques
- 🔴 **Cutting-Edge** - Active research area
- ⏱️ **Maturity** - Production readiness
- 📅 **Updated** - Last verified
- 🔬 **Experimental** - Research-only
- 🏭 **Production** - Industry-proven

---

## 🎯 RLHF (Reinforcement Learning from Human Feedback)

### InstructGPT Paper
- **URL:** https://arxiv.org/abs/2203.02155
- **Title:** Training language models to follow instructions with human feedback
- **Authors:** Ouyang et al. (OpenAI)
- **Year:** 2022
- **Note:** Original RLHF paper for instruction following.

### PPO: Proximal Policy Optimization
- **URL:** https://arxiv.org/abs/1707.06347
- **Title:** Proximal Policy Optimization Algorithms
- **Authors:** Schulman et al. (OpenAI)
- **Year:** 2017
- **Note:** RL algorithm used in RLHF training.

### TRL: Transformer Reinforcement Learning
- **URL:** https://github.com/huggingface/trl
- **Type:** Library
- **License:** Apache 2.0
- **Note:** PPO, DPO, RLHF implementations for transformers.

### RLHF: Reinforcement Learning from Human Feedback
- **URL:** https://huyenchip.com/2023/05/02/rlhf.html
- **Type:** Blog Post
- **Author:** Chip Huyen
- **Note:** Comprehensive RLHF overview.

---

## 🎨 Direct Preference Optimization (DPO)

### DPO Paper
- **URL:** https://arxiv.org/abs/2305.18290
- **Title:** Direct Preference Optimization: Your Language Model is Secretly a Reward Model
- **Authors:** Rafailov et al. (Stanford)
- **Year:** 2023
- **Note:** Simpler alternative to RLHF without RL.

### Zephyr: Direct Distillation of LM Alignment
- **URL:** https://arxiv.org/abs/2310.16944
- **Type:** Paper + Model
- **Year:** 2023
- **Note:** DPO-trained 7B model achieving strong performance.

### ORPO: Monolithic Preference Optimization
- **URL:** https://arxiv.org/abs/2403.07691
- **Type:** Paper
- **Year:** 2024
- **Note:** Single-stage alignment without reference model.

---

## 🛡️ AI Safety & Alignment

### Constitutional AI Paper
- **URL:** https://arxiv.org/abs/2212.08073
- **Title:** Constitutional AI: Harmlessness from AI Feedback
- **Authors:** Bai et al. (Anthropic)
- **Year:** 2022
- **Note:** Self-supervised alignment using principles.

### Red Teaming Language Models
- **URL:** https://arxiv.org/abs/2202.03286
- **Title:** Red Teaming Language Models to Reduce Harms
- **Authors:** Perez et al. (Anthropic)
- **Year:** 2022
- **Note:** Finding failure modes through adversarial testing.

### NeMo Guardrails
- **URL:** https://github.com/NVIDIA/NeMo-Guardrails
- **Type:** Framework
- **Maintainer:** NVIDIA
- **License:** Apache 2.0
- **Note:** Add safety rails to LLM applications.

### Anthropic's Core Views on AI Safety
- **URL:** https://www.anthropic.com/index/core-views-on-ai-safety
- **Type:** Article
- **Note:** Alignment research perspectives from Anthropic.

---

## 🖼️ Multimodal Models

### CLIP: Connecting Text and Images
- **URL:** https://arxiv.org/abs/2103.00020
- **Title:** Learning Transferable Visual Models From Natural Language Supervision
- **Authors:** Radford et al. (OpenAI)
- **Year:** 2021
- **Note:** Contrastive learning for vision-language models.

### LLaVA: Large Language and Vision Assistant
- **URL:** https://arxiv.org/abs/2304.08485
- **Type:** Paper + Model
- **Year:** 2023
- **Note:** Open-source vision-language model.

### LLaVA GitHub
- **URL:** https://github.com/haotian-liu/LLaVA
- **Type:** Code Repository
- **License:** Apache 2.0
- **Note:** Training and inference code for LLaVA.

### Flamingo: Visual Language Model
- **URL:** https://arxiv.org/abs/2204.14198
- **Title:** Flamingo: a Visual Language Model for Few-Shot Learning
- **Authors:** Alayrac et al. (DeepMind)
- **Year:** 2022
- **Note:** Few-shot learning with interleaved vision-text.

### GPT-4 Vision (GPT-4V) System Card
- **URL:** https://openai.com/research/gpt-4v-system-card
- **Type:** Technical Report
- **Year:** 2023
- **Note:** Multimodal GPT-4 capabilities and safety.

### Gemini: Multimodal from the Ground Up
- **URL:** https://arxiv.org/abs/2312.11805
- **Title:** Gemini: A Family of Highly Capable Multimodal Models
- **Authors:** Gemini Team (Google)
- **Year:** 2023
- **Note:** Natively multimodal model architecture.

---

## 🎤 Speech & Audio

### Whisper: Robust Speech Recognition
- **URL:** https://github.com/openai/whisper
- **Type:** Model + Code
- **Maintainer:** OpenAI
- **License:** MIT
- **Note:** Multilingual speech recognition.

### AudioCraft
- **URL:** https://github.com/facebookresearch/audiocraft
- **Type:** Framework
- **Maintainer:** Meta AI
- **License:** MIT
- **Note:** Audio generation (MusicGen, AudioGen).

### VALL-E: Neural Codec Language Model
- **URL:** https://arxiv.org/abs/2301.02111
- **Title:** VALL-E: Neural Codec Language Models are Zero-Shot Text to Speech Synthesizers
- **Authors:** Wang et al. (Microsoft)
- **Year:** 2023
- **Note:** Text-to-speech with voice cloning.

---

## 🧪 Reasoning & Problem Solving

### Chain-of-Thought Prompting
- **URL:** https://arxiv.org/abs/2201.11903
- **Title:** Chain-of-Thought Prompting Elicits Reasoning
- **Year:** 2022
- **Note:** Eliciting reasoning through intermediate steps.

### Tree of Thoughts
- **URL:** https://arxiv.org/abs/2305.10601
- **Title:** Tree of Thoughts: Deliberate Problem Solving
- **Year:** 2023
- **Note:** Explore multiple reasoning paths like tree search.

### Self-Consistency
- **URL:** https://arxiv.org/abs/2203.11171
- **Title:** Self-Consistency Improves Chain of Thought Reasoning
- **Year:** 2022
- **Note:** Sample diverse paths and select consistent answer.

### Graph of Thoughts
- **URL:** https://arxiv.org/abs/2308.09687
- **Title:** Graph of Thoughts: Solving Problems with Large Language Models
- **Year:** 2023
- **Note:** Model reasoning as arbitrary graph structures.

---

## 🧠 In-Context Learning

### What Can Transformers Learn In-Context?
- **URL:** https://arxiv.org/abs/2402.08137
- **Title:** What Can Transformers Learn In-Context? A Case Study
- **Year:** 2024
- **Note:** Mechanistic understanding of in-context learning.

### Rethinking the Role of Demonstrations
- **URL:** https://arxiv.org/abs/2202.12837
- **Title:** Rethinking the Role of Demonstrations in In-Context Learning
- **Year:** 2022
- **Note:** What matters in few-shot prompting.

---

## 🔍 Interpretability & Mechanistic Analysis

### Anthropic Interpretability Research
- **URL:** https://www.anthropic.com/index?subjects=interpretability
- **Type:** Research Articles
- **Note:** Mechanistic interpretability papers and findings.

### TransformerLens
- **URL:** https://github.com/neelnanda-io/TransformerLens
- **Type:** Library
- **License:** MIT
- **Note:** Reverse engineering transformer internals.

### Circuits in Neural Networks
- **URL:** https://distill.pub/2020/circuits/
- **Type:** Article Series
- **Note:** Visual explanations of neural network features.

---

## 📊 Long Context Models

### Rotary Position Embedding (RoPE)
- **URL:** https://arxiv.org/abs/2104.09864
- **Title:** RoFormer: Enhanced Transformer with Rotary Position Embedding
- **Year:** 2021
- **Note:** Position encoding enabling length extrapolation.

### YaRN: Efficient Context Window Extension
- **URL:** https://arxiv.org/abs/2309.00071
- **Title:** YaRN: Efficient Context Window Extension of LLMs
- **Year:** 2023
- **Note:** Extend context length without retraining.

### LongLoRA: Efficient Fine-tuning of Long-Context LLMs
- **URL:** https://arxiv.org/abs/2309.12307
- **Type:** Paper
- **Year:** 2023
- **Note:** Efficient adaptation for long context.

---

## 🌍 Multilingual Models

### mBERT: Multilingual BERT
- **URL:** https://github.com/google-research/bert/blob/master/multilingual.md
- **Type:** Model
- **Maintainer:** Google
- **Note:** BERT trained on 104 languages.

### XLM-RoBERTa
- **URL:** https://huggingface.co/xlm-roberta-large
- **Type:** Model
- **Note:** Cross-lingual model trained on 100 languages.

### BLOOM
- **URL:** https://huggingface.co/bigscience/bloom
- **Type:** Model
- **License:** BigScience RAIL License
- **Note:** 176B multilingual model (46 languages).

### mT5: Multilingual T5
- **URL:** https://arxiv.org/abs/2010.11934
- **Title:** mT5: A Massively Multilingual Pre-trained Text-to-Text Transformer
- **Year:** 2020
- **Note:** T5 trained on 101 languages.

---

## 🔐 Privacy & Federated Learning

### DP-SGD: Differentially Private Training
- **URL:** https://arxiv.org/abs/1607.00133
- **Title:** Deep Learning with Differential Privacy
- **Year:** 2016
- **Note:** Training with formal privacy guarantees.

### Federated Learning for NLP
- **URL:** https://arxiv.org/abs/1906.04329
- **Title:** Federated Learning for Mobile Keyboard Prediction
- **Authors:** Hard et al. (Google)
- **Year:** 2019
- **Note:** Privacy-preserving distributed training.

---

## 🎯 Mixture of Experts (MoE)

### Mixtral 8x7B
- **URL:** https://arxiv.org/abs/2401.04088
- **Title:** Mixtral of Experts
- **Authors:** Jiang et al. (Mistral AI)
- **Year:** 2024
- **Note:** Sparse MoE with 8 experts, 47B total params, 13B active.

### Switch Transformers
- **URL:** https://arxiv.org/abs/2101.03961
- **Title:** Switch Transformers: Scaling to Trillion Parameter Models
- **Authors:** Fedus et al. (Google)
- **Year:** 2021
- **Note:** Simplified MoE architecture scaling to trillions of parameters.

---

## 📚 Learning Resources

### Alignment Newsletter
- **URL:** https://alignment-newsletter.libsyn.com/
- **Type:** Newsletter
- **Note:** Weekly updates on AI alignment research.

### AI Safety Newsletter
- **URL:** https://newsletter.safe.ai/
- **Type:** Newsletter
- **Note:** Curated AI safety news and research.

### Anthropic Research
- **URL:** https://www.anthropic.com/research
- **Type:** Research Articles
- **Note:** Latest alignment and safety research.

### OpenAI Research
- **URL:** https://openai.com/research
- **Type:** Research Articles
- **Note:** Latest LLM and multimodal research.
