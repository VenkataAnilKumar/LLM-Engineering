# 🗃️ Free Datasets for LLM Research

A comprehensive collection of free, open-source datasets for training, fine-tuning, and evaluating Large Language Models.

---

## 🎯 Overview

This directory contains curated lists of:
- **Pre-training datasets** - Large-scale text corpora
- **Instruction tuning datasets** - Instruction-following examples
- **Fine-tuning datasets** - Task-specific data
- **Evaluation benchmarks** - Test sets for assessment
- **Multilingual datasets** - Non-English resources
- **Domain-specific datasets** - Specialized domains

---

## 📚 Large-Scale Pre-training Datasets

### 🌟 **The Pile** (EleutherAI)
**Size**: 825 GB of text  
**Link**: https://pile.eleuther.ai/  
**License**: Open

**Components** (22 sources):
- Books3 (literature)
- OpenWebText2 (web)
- ArXiv (scientific papers)
- GitHub (code)
- StackExchange (Q&A)
- Wikipedia
- And 16 more...

**Why Important**: High-quality, diverse pre-training corpus used by many open models.

---

### **C4: Colossal Clean Crawled Corpus**
**Size**: 750+ GB  
**Link**: https://www.tensorflow.org/datasets/catalog/c4  
**Source**: Common Crawl

**Features**:
- Cleaned and filtered web text
- English-focused
- Used by T5, GPT-Neo, etc.
- Multiple variants available

**Variants**:
- en (English)
- realnewslike (news-style)
- multilingual versions

---

### **RedPajama**
**Size**: 1.2+ trillion tokens  
**Link**: https://github.com/togethercomputer/RedPajama-Data  
**License**: Apache 2.0

**Components**:
- CommonCrawl
- C4
- GitHub
- Books
- ArXiv
- Wikipedia
- StackExchange

**Why Important**: Open reproduction of LLaMA training set.

---

### **ROOTS Corpus** (BigScience)
**Size**: 1.6 TB  
**Link**: https://huggingface.co/bigscience-data  
**Languages**: 59 languages

**Used by**: BLOOM model

**Features**:
- Multilingual and diverse
- Carefully curated
- Documented data sources

---

### **Dolma**
**Size**: 3 trillion tokens  
**Link**: https://huggingface.co/datasets/allenai/dolma  
**License**: AI2 ImpACT License

**Features**:
- Web crawl
- Code
- Scientific papers
- Books
- Social media

**Creator**: Allen Institute for AI

---

## 🎓 Instruction Tuning Datasets

### 🌟 **Alpaca Dataset** (Stanford)
**Size**: 52K instruction-response pairs  
**Link**: https://github.com/tatsu-lab/stanford_alpaca  
**License**: CC BY NC 4.0

**Format**:
```json
{
  "instruction": "Give three tips for staying healthy.",
  "input": "",
  "output": "1. Eat a balanced diet..."
}
```

**Why Important**: Enabled instruction-tuned LLaMA (Alpaca model).

---

### **Dolly Dataset** (Databricks)
**Size**: 15K examples  
**Link**: https://huggingface.co/datasets/databricks/databricks-dolly-15k  
**License**: CC BY-SA 3.0

**Features**:
- Human-generated
- No GPT-based data
- Commercial use allowed
- 7 categories

---

### **OpenAssistant Conversations**
**Size**: 161K messages  
**Link**: https://huggingface.co/datasets/OpenAssistant/oasst1  
**License**: Apache 2.0

**Features**:
- Multi-turn conversations
- Human feedback
- Multiple languages (35+)
- Quality ratings

---

### **ShareGPT**
**Size**: Varies (multiple versions)  
**Link**: https://huggingface.co/datasets/RyokoAI/ShareGPT52K  
**Source**: User-shared conversations

**Format**: Multi-turn chat conversations

**Note**: Quality varies, filter carefully

---

### **FLAN Collection** (Google)
**Size**: 1800+ tasks  
**Link**: https://github.com/google-research/FLAN  
**License**: Apache 2.0

**Contents**:
- Muffin
- CoT
- Dialog
- NIv2 (Natural Instructions v2)

**Used by**: FLAN-T5, FLAN-PaLM

---

## 📊 Benchmark Datasets

### **MMLU** (Massive Multitask Language Understanding)
**Size**: 15,908 questions  
**Link**: https://github.com/hendrycks/test  
**Subjects**: 57

**Categories**: STEM, Humanities, Social Sciences, Other

---

### **HellaSwag**
**Size**: 70K problems  
**Link**: https://rowanzellers.com/hellaswag/

**Task**: Sentence completion with commonsense reasoning

---

### **TruthfulQA**
**Size**: 817 questions  
**Link**: https://github.com/sylinrl/TruthfulQA

**Purpose**: Measure truthfulness of model responses

---

### **HumanEval** (Code)
**Size**: 164 problems  
**Link**: https://github.com/openai/human-eval

**Language**: Python programming

---

### **GSM8K** (Math)
**Size**: 8,500 problems  
**Link**: https://github.com/openai/grade-school-math

**Level**: Grade school math word problems

---

## 💬 Dialogue & Conversation

### **MultiWOZ** (Task-Oriented Dialogue)
**Size**: 10K dialogues  
**Link**: https://github.com/budzianowski/multiwoz  
**Domains**: 7 (restaurant, hotel, taxi, etc.)

---

### **PersonaChat**
**Size**: 164K utterances  
**Link**: https://github.com/facebookresearch/ParlAI/tree/main/projects/personachat

**Features**: Personality-based conversations

---

### **DailyDialog**
**Size**: 13K dialogues  
**Link**: https://huggingface.co/datasets/daily_dialog

**Style**: Daily conversations, emotionally annotated

---

## 📝 Summarization

### **CNN/DailyMail**
**Size**: 300K+ article-summary pairs  
**Link**: https://huggingface.co/datasets/cnn_dailymail  
**License**: Apache 2.0

**Use**: News summarization

---

### **XSum** (Extreme Summarization)
**Size**: 227K articles  
**Link**: https://github.com/EdinburghNLP/XSum

**Style**: Single-sentence summaries

---

### **SAMSum** (Dialogue Summarization)
**Size**: 16K conversations  
**Link**: https://huggingface.co/datasets/samsum

**Domain**: Messenger-like conversations

---

## 🌍 Multilingual Datasets

### **mC4** (Multilingual C4)
**Languages**: 100+  
**Link**: https://huggingface.co/datasets/mc4  
**Size**: Varies by language

---

### **OSCAR**
**Languages**: 166  
**Link**: https://oscar-project.org/  
**Source**: Common Crawl

---

### **CC100**
**Languages**: 100  
**Link**: https://data.statmt.org/cc-100/  
**Size**: 2.5TB total

---

### **FLORES-200**
**Languages**: 200  
**Link**: https://github.com/facebookresearch/flores  
**Use**: Translation evaluation

---

## 💻 Code Datasets

### **The Stack**
**Size**: 6TB  
**Link**: https://huggingface.co/datasets/bigcode/the-stack  
**Languages**: 358 programming languages

**License**: Per-repository (mostly permissive)

---

### **CodeParrot**
**Size**: 50GB  
**Link**: https://huggingface.co/datasets/codeparrot/github-code  
**Language**: Python

---

### **CodeSearchNet**
**Size**: 6M functions  
**Link**: https://github.com/github/CodeSearchNet  
**Languages**: 6 programming languages

---

## 📖 Question Answering

### **SQuAD** (Stanford QA Dataset)
**Size**: 100K+ questions  
**Link**: https://rajpurkar.github.io/SQuAD-explorer/  
**Versions**: 1.1, 2.0

---

### **Natural Questions** (Google)
**Size**: 300K+ questions  
**Link**: https://ai.google.com/research/NaturalQuestions  
**Source**: Real Google searches

---

### **TriviaQA**
**Size**: 650K question-answer pairs  
**Link**: http://nlp.cs.washington.edu/triviaqa/

---

## 🔬 Scientific & Technical

### **PubMed Abstracts**
**Size**: 30M+ abstracts  
**Link**: https://pubmed.ncbi.nlm.nih.gov/  
**Domain**: Biomedical

---

### **ArXiv Dataset**
**Size**: 2M+ papers  
**Link**: https://www.kaggle.com/Cornell-University/arxiv  
**Domain**: Scientific preprints

---

### **PubMed Central Open Access**
**Size**: 3M+ full-text articles  
**Link**: https://www.ncbi.nlm.nih.gov/pmc/tools/openftlist/

---

## 📰 News & Articles

### **AG News**
**Size**: 120K articles  
**Link**: https://huggingface.co/datasets/ag_news  
**Categories**: 4

---

### **20 Newsgroups**
**Size**: 20K documents  
**Link**: http://qwone.com/~jason/20Newsgroups/  
**Categories**: 20

---

## 🎭 Creative Writing

### **WritingPrompts**
**Size**: 300K prompt-story pairs  
**Link**: https://www.kaggle.com/ratthachat/writing-prompts  
**Source**: Reddit r/WritingPrompts

---

### **BookCorpus**
**Size**: 11K books  
**Note**: Original unavailable, alternatives exist

---

## 🏥 Domain-Specific

### Medical
- **MIMIC-III**: Clinical notes (requires credentialing)
- **PubMedQA**: Medical questions
- **MedQA**: Medical exams

### Legal
- **CaseHOLD**: Legal citation prediction
- **LegalBench**: Legal reasoning

### Finance
- **FinQA**: Financial reasoning
- **FiQA**: Financial QA

---

## 🛠️ Dataset Tools & Platforms

### **Hugging Face Datasets**
**Link**: https://huggingface.co/datasets  
**Count**: 100,000+ datasets

**Features**:
- Easy download
- Streaming support
- Unified API
- Free hosting

---

### **Kaggle Datasets**
**Link**: https://www.kaggle.com/datasets  
**Count**: 50,000+ datasets

**Features**:
- Community-driven
- Free compute
- Competitions

---

### **Papers with Code Datasets**
**Link**: https://paperswithcode.com/datasets  
**Features**: Dataset + benchmark tracking

---

## 📋 Dataset Selection Guide

### For Pre-training
✅ Large and diverse (100GB+)  
✅ High quality  
✅ Properly deduplicated  
✅ Multiple domains  

**Recommended**: The Pile, RedPajama, C4

---

### For Instruction Tuning
✅ High-quality examples (1K-100K)  
✅ Diverse tasks  
✅ Clear instructions  
✅ Safe content  

**Recommended**: Alpaca, Dolly, OpenAssistant

---

### For Fine-tuning
✅ Domain-relevant  
✅ High quality  
✅ Sufficient size (500+)  
✅ Representative  

**Choose based on your domain**

---

### For Evaluation
✅ Held-out test set  
✅ No training contamination  
✅ Diverse coverage  
✅ Human-verified  

**Recommended**: MMLU, HellaSwag, HumanEval

---

## ⚖️ Legal & Ethical Considerations

### Licenses to Check
- ✅ Commercial use allowed?
- ✅ Attribution required?
- ✅ Derivatives allowed?
- ✅ Share-alike requirements?

### Common Licenses
- **Apache 2.0**: Very permissive
- **MIT**: Very permissive
- **CC BY**: Attribution required
- **CC BY-SA**: Attribution + share-alike
- **CC BY-NC**: Non-commercial only

### Data Ethics
⚠️ Check for PII (Personal Identifiable Information)  
⚠️ Verify consent for collection  
⚠️ Audit for biases  
⚠️ Respect opt-outs  
⚠️ Consider environmental impact  

---

## 🔧 Data Processing Tips

### Cleaning
1. Remove duplicates
2. Filter low-quality content
3. Remove PII
4. Fix encoding issues
5. Normalize formatting

### Quality Checks
- Length distribution
- Language detection
- Toxicity filtering
- Perplexity filtering

### Tools
- **[datatrove](https://github.com/huggingface/datatrove)** - Hugging Face
- **[text-fabric](https://github.com/google-research/text-fabric)** - Google

---

## 📊 Dataset Statistics Template

When documenting a dataset, include:
- **Size**: Number of examples, tokens, GB
- **Domain**: Topic/field
- **Language**: Supported languages
- **License**: Usage terms
- **Quality**: Collection method, filtering
- **Splits**: Train/dev/test
- **Format**: JSON, text, parquet, etc.

---

## 🚀 Contributing

Found a great dataset? Contribute:
1. Verify it's free and open
2. Check the license
3. Test the quality
4. Add documentation
5. Submit a PR!

---

<div align="center">

**[⬆ Back to Top](#-free-datasets-for-llm-research)**

*"Quality data is the foundation of quality models."*

</div>
