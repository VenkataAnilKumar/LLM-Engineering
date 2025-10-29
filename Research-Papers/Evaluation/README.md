# 📄 Research Papers - Evaluation

Curated research papers on evaluating, benchmarking, and analyzing Large Language Models.

---

## 🎯 Overview

Topics covered:
- Benchmark datasets and metrics
- Reasoning and knowledge evaluation
- Safety and bias assessment
- Multilingual evaluation
- Domain-specific benchmarks
- Human vs. automatic evaluation

---

## 📊 General Benchmarks

### 🌟 **GLUE: A Multi-Task Benchmark** (2018)
**Link**: https://arxiv.org/abs/1804.07461  
**Impact**: ⭐⭐⭐⭐⭐

**Tasks** (9 total):
- Sentiment analysis
- Paraphrase detection
- Textual entailment
- Question answering
- Linguistic acceptability

**Why Important**: Standard benchmark for pre-BERT era.

---

### 🌟 **SuperGLUE: A More Challenging Benchmark** (2019)
**Link**: https://arxiv.org/abs/1905.00537  
**Impact**: ⭐⭐⭐⭐⭐

**Improvements**:
- More difficult tasks
- 8 tasks
- Human baseline harder to beat
- Better discrimination

**Status**: Mostly solved by modern LLMs.

---

### 🌟 **MMLU: Measuring Massive Multitask Language Understanding** (2020)
**Link**: https://arxiv.org/abs/2009.03300  
**Impact**: ⭐⭐⭐⭐⭐

**Coverage**:
- 57 subjects
- Elementary to professional level
- STEM, humanities, social sciences
- 15,908 multiple-choice questions

**Why Important**: Current standard for measuring general knowledge and reasoning.

---

### **BIG-bench: Beyond the Imitation Game Benchmark** (2022)
**Link**: https://arxiv.org/abs/2206.04615  
**Impact**: ⭐⭐⭐⭐

**Features**:
- 200+ diverse tasks
- Collaborative creation
- Focus on future capabilities
- Identifies emergent abilities

---

## 🧠 Reasoning Evaluation

### 🌟 **HellaSwag: Can a Machine Really Finish Your Sentence?** (2019)
**Link**: https://arxiv.org/abs/1905.07830  
**Impact**: ⭐⭐⭐⭐

**Task**: Commonsense reasoning for sentence completion

**Challenge**: Adversarially constructed to fool models

**Usage**: Standard reasoning benchmark

---

### **ARC: AI2 Reasoning Challenge** (2018)
**Link**: https://arxiv.org/abs/1803.05457  
**Impact**: ⭐⭐⭐⭐

**Content**:
- Science exam questions
- Elementary and middle school level
- Requires reasoning + knowledge
- Easy and Challenge sets

---

### **WinoGrande: Adversarial Winograd Schema Challenge** (2019)
**Link**: https://arxiv.org/abs/1907.10641  
**Impact**: ⭐⭐⭐⭐

**Task**: Pronoun resolution requiring common sense

**Size**: 44k problems

**Difficulty**: Adversarially designed

---

### **GSM8K: Grade School Math Word Problems** (2021)
**Link**: https://arxiv.org/abs/2110.14168  
**Impact**: ⭐⭐⭐⭐

**Focus**: Multi-step mathematical reasoning

**Problems**: 8,500 grade school math questions

**Why Important**: Tests reasoning chains, not just pattern matching

---

### **MATH: Measuring Mathematical Problem Solving** (2021)
**Link**: https://arxiv.org/abs/2103.03874  
**Impact**: ⭐⭐⭐⭐

**Content**:
- 12,500 competition mathematics problems
- 7 subjects (algebra, geometry, etc.)
- Step-by-step solutions
- Very challenging

---

## 💬 Language Understanding

### **TruthfulQA: Measuring Truthfulness** (2021)
**Link**: https://arxiv.org/abs/2109.07958  
**Impact**: ⭐⭐⭐⭐

**Purpose**: Test tendency to generate false statements

**Coverage**: 817 questions spanning 38 categories

**Finding**: Larger models sometimes less truthful

---

### **Natural Questions** (Google, 2019)
**Link**: https://arxiv.org/abs/1901.08634  
**Impact**: ⭐⭐⭐⭐

**Source**: Real Google search queries

**Format**: Question + Wikipedia passage + annotations

**Size**: 300k+ questions

---

### **SQuAD: Stanford Question Answering Dataset** (2016)
**Link**: https://arxiv.org/abs/1606.05250  
**Impact**: ⭐⭐⭐⭐⭐

**Task**: Reading comprehension

**Format**: Questions + context paragraphs

**Versions**: SQuAD 1.1, SQuAD 2.0 (with unanswerable)

---

## 💻 Code Evaluation

### 🌟 **HumanEval: Evaluating Code Generation** (2021)
**Link**: https://arxiv.org/abs/2107.03374  
**Impact**: ⭐⭐⭐⭐⭐

**Content**:
- 164 Python programming problems
- Function signature + docstring
- Unit tests for verification

**Standard**: De facto standard for code evaluation

---

### **MBPP: Mostly Basic Python Problems** (2021)
**Link**: https://arxiv.org/abs/2108.07732  
**Impact**: ⭐⭐⭐⭐

**Content**:
- 974 Python programming problems
- Entry-level difficulty
- 3 test cases each

---

### **CodeXGLUE** (Microsoft, 2021)
**Link**: https://arxiv.org/abs/2102.04664  
**Impact**: ⭐⭐⭐⭐

**Tasks**: 14 diverse code intelligence tasks

**Coverage**: Generation, understanding, translation

---

## 🌍 Multilingual Evaluation

### **XNLI: Cross-lingual Natural Language Inference** (2018)
**Link**: https://arxiv.org/abs/1809.05053  
**Impact**: ⭐⭐⭐⭐

**Languages**: 15 languages

**Task**: Textual entailment

**Use**: Cross-lingual transfer evaluation

---

### **FLORES: Low-Resource Translation** (2021)
**Link**: https://arxiv.org/abs/2106.03193  
**Impact**: ⭐⭐⭐⭐

**Coverage**: 200+ languages

**Focus**: Low-resource languages

**Impact**: Multilingual LLM evaluation

---

## ⚖️ Safety & Bias

### 🌟 **RealToxicityPrompts** (2020)
**Link**: https://arxiv.org/abs/2009.11462  
**Impact**: ⭐⭐⭐⭐

**Purpose**: Measure toxicity in generation

**Dataset**: 100k prompts from web

**Tool**: Perspective API for scoring

---

### **BBQ: Bias Benchmark for QA** (2022)
**Link**: https://arxiv.org/abs/2110.08193  
**Impact**: ⭐⭐⭐⭐

**Focus**: Social bias measurement

**Categories**: 11 categories (age, gender, race, etc.)

**Design**: Ambiguous and unambiguous contexts

---

### **WinoGender: Gender Bias in Coreference** (2018)
**Link**: https://arxiv.org/abs/1804.09301  
**Impact**: ⭐⭐⭐⭐

**Task**: Pronoun resolution

**Purpose**: Detect gender stereotypes

**Impact**: Widely used bias benchmark

---

### **ToxiGen: Large-Scale Machine-Generated Dataset** (2022)
**Link**: https://arxiv.org/abs/2203.09509  
**Impact**: ⭐⭐⭐

**Content**: Implicitly toxic statements

**Coverage**: 13 minority groups

**Purpose**: Subtle toxicity detection

---

## 🔬 Comprehensive Evaluation

### 🌟 **HELM: Holistic Evaluation of Language Models** (2022)
**Authors**: Stanford CRFM  
**Link**: https://arxiv.org/abs/2211.09110  
**Impact**: ⭐⭐⭐⭐⭐

**Approach**:
- 42 scenarios
- 7 metrics categories
- Transparency and standardization
- Holistic view

**Metrics**:
- Accuracy
- Calibration
- Robustness
- Fairness
- Bias
- Toxicity
- Efficiency

**Website**: https://crfm.stanford.edu/helm/

---

### **Open LLM Leaderboard** (Hugging Face)
**Link**: https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard

**Benchmarks**:
- ARC
- HellaSwag
- MMLU
- TruthfulQA

**Purpose**: Compare open-source models

---

## 📈 Evaluation Metrics

### Automatic Metrics

**Perplexity**:
- Language modeling quality
- Lower is better
- Not always correlates with quality

**BLEU** (Translation):
- N-gram overlap
- 0-100 scale
- Standard for MT

**ROUGE** (Summarization):
- Recall-oriented
- Multiple variants (ROUGE-1, ROUGE-L)
- N-gram and sequence matching

**F1 Score** (Classification):
- Harmonic mean of precision and recall
- 0-1 scale

**Exact Match** (QA):
- Binary: correct or not
- Strict metric

---

### Human Evaluation

**Dimensions**:
- Fluency
- Coherence
- Relevance
- Factuality
- Safety
- Helpfulness

**Challenges**:
- Expensive
- Subjective
- Hard to scale
- Inter-annotator agreement

---

## 🎯 Domain-Specific Benchmarks

### Medical
**MedQA, PubMedQA, MedMCQA**:
- Medical question answering
- Clinical reasoning
- Biomedical knowledge

### Legal
**LegalBench**:
- Legal reasoning
- Contract understanding
- Case analysis

### Finance
**FinQA, ConvFinQA**:
- Financial reasoning
- Numerical reasoning
- Report understanding

---

## 🔧 Evaluation Tools

### **lm-evaluation-harness** (EleutherAI)
**Link**: https://github.com/EleutherAI/lm-evaluation-harness

**Features**:
- Standardized evaluation
- 200+ tasks
- Easy to use
- Reproducible

---

### **Hugging Face Evaluate**
**Link**: https://huggingface.co/docs/evaluate/

**Features**:
- Metric library
- Easy integration
- Multiple metrics
- Well-documented

---

## 📊 Best Practices

### Comprehensive Evaluation
✅ Use multiple benchmarks  
✅ Include safety/bias metrics  
✅ Test edge cases  
✅ Consider domain-specific tasks  

### Reproducibility
✅ Report exact versions  
✅ Share prompts  
✅ Document hyperparameters  
✅ Use standard splits  

### Interpretation
✅ Don't rely on single metric  
✅ Understand limitations  
✅ Compare to baselines  
✅ Consider human evaluation  

### Reporting
✅ Report confidence intervals  
✅ Include failure analysis  
✅ Discuss limitations  
✅ Share negative results  

---

## 🚨 Common Pitfalls

❌ **Cherry-picking**: Reporting only best results  
❌ **Data contamination**: Test data in training  
❌ **Prompt engineering**: Unfair optimization  
❌ **Single metric focus**: Ignoring other aspects  
❌ **Ignoring efficiency**: Only focusing on accuracy  

---

## 📚 Important Meta-Papers

### **On the Dangers of Stochastic Parrots** (2021)
**Link**: https://dl.acm.org/doi/10.1145/3442188.3445922  
**Impact**: ⭐⭐⭐⭐⭐

**Topics**:
- Environmental costs
- Training data biases
- Risks of large models
- Ethical considerations

---

### **Evaluating Large Language Models Trained on Code** (2021)
**Link**: https://arxiv.org/abs/2107.03374  
**Impact**: ⭐⭐⭐⭐

**Contributions**:
- Code evaluation methodology
- HumanEval benchmark
- Best practices

---

### **A Survey of Evaluation Metrics for NLG** (2020)
**Link**: https://arxiv.org/abs/2008.12009  
**Impact**: ⭐⭐⭐

**Coverage**:
- Automatic metrics
- Human evaluation
- Correlation studies
- Recommendations

---

## 🎓 Future Directions

**Emerging Areas**:
- Long-context evaluation
- Multimodal benchmarks
- Agentic capabilities
- Tool use assessment
- Reasoning depth
- Factuality verification

---

<div align="center">

**[⬅️ Training Techniques](../Training-Techniques/)** | **[⬆ Back to Top](#-research-papers---evaluation)**

</div>
