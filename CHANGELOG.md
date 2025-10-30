# Changelog

All notable changes to the LLM Engineering Roadmap will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.5.0] - 2025-10-30

### 📚 Final Core Categories Added

#### New Categories

**12-Research-Papers/**
- Comprehensive collection of must-read papers organized by topic
- Foundational papers: Attention Is All You Need, BERT, GPT-2, GPT-3
- Transformer architecture: Transformer-XL, Reformer, Flash Attention
- Large language models: LLaMA, LLaMA 2, Mistral, Mixtral
- Fine-tuning & adaptation: LoRA, QLoRA, Prefix-Tuning, Adapters
- Prompt engineering: Chain-of-Thought, ReAct, Tree of Thoughts, Lost in the Middle
- RAG: Original RAG paper, Sentence-BERT, DPR, Self-RAG
- Alignment & RLHF: InstructGPT, Constitutional AI, DPO, RLAIF
- Efficient training: 8-bit optimizers, ZeRO, Flash Attention, vLLM
- Evaluation: MMLU, HumanEval, TruthfulQA, HELM
- Multimodal: CLIP, Flamingo, GPT-4 Vision
- Safety: Red Teaming, Adversarial Attacks, Transparency Index
- 4 curated reading lists by role (Beginners, ML Engineers, Researchers, App Developers)
- Paper reading strategy guide (3-pass method)
- 50+ essential papers with summaries, key contributions, reading time estimates

**13-Community/**
- Discord servers: Hugging Face, OpenAI, LangChain, LlamaIndex, LocalLLaMA, EleutherAI
- Reddit communities: r/LocalLLaMA, r/MachineLearning, r/ArtificialIntelligence
- Twitter/X accounts to follow: Researchers (Karpathy, Ng, LeCun), Educators (Alammar, Saravia), Builders (Chase, Willison)
- Newsletters: The Batch, Import AI, TLDR AI, Ben's Bites, Alpha Signal, LLM Weekly
- Podcasts: The AI Podcast, Practical AI, TWIML AI, Latent Space
- YouTube channels: Karpathy, 3Blue1Brown, StatQuest
- Blogs: Company blogs (OpenAI, Anthropic, Google, Meta, HF) and personal blogs (Lilian Weng, Jay Alammar)
- Conferences: NeurIPS, ICML, ACL, EMNLP, ICLR, AI Engineer Summit
- Open source contribution opportunities
- Study groups and local meetups
- Getting help guide (Stack Overflow, forums, Discord, Reddit)
- Community etiquette and best practices
- 4-week community engagement plan

#### Updated Files
- **README.md**: Added links to categories 12-13, updated What's Inside table
- **CHANGELOG.md**: Documented v2.5.0 additions

#### Summary of v2.5.0
- **2 new essential categories** (Research Papers, Community)
- **50+ research papers** with summaries and reading guides
- **4 role-specific reading lists** (15-55 hours each)
- **100+ community resources** (Discord, Reddit, newsletters, conferences)
- **Complete learning ecosystem** from papers to community engagement
- **Repository now feature-complete** with 13 core categories + case studies

---

## [2.4.0] - 2025-10-30

### 🚀 New Categories & Supporting Documentation

#### New Categories Added

**10-Benchmarks/**
- Comprehensive evaluation and benchmarking guide
- General knowledge benchmarks: MMLU, HellaSwag, ARC, TruthfulQA, Winogrande
- Code benchmarks: HumanEval, MBPP, MultiPL-E, DS-1000
- Math benchmarks: GSM8K, MATH
- Reading comprehension: SQuAD, DROP, QuAC
- Multilingual: XNLI, FLORES-101, Belebele
- Safety & bias: BBQ, RealToxicityPrompts, ToxiGen
- Factuality: FEVER, HaluEval
- Agent benchmarks: WebArena, AgentBench, GAIA
- Major leaderboards: Open LLM Leaderboard, ChatBot Arena, AlpacaEval, MT-Bench
- Evaluation frameworks: lm-evaluation-harness, OpenAI Evals, DeepEval, promptfoo, HELM
- 5 comparison tables for benchmarks and frameworks
- Best practices for evaluation

**11-Tools-and-Utilities/**
- Essential development tools directory
- IDEs & editors: VS Code, Cursor, PyCharm, Jupyter, Colab, Kaggle
- IDE extensions: GitHub Copilot, Continue, Codeium, Tabnine
- CLI tools: llm, aichat, shell-genie, mods
- Debugging & profiling: W&B, TensorBoard, PyTorch Profiler
- Monitoring & logging: LangSmith, Phoenix, LangFuse, Helicone
- Version control: DVC, MLflow, Hugging Face Hub, Git LFS
- Prompt engineering tools
- Dataset tools: Label Studio, cleanlab
- Testing: DeepEval, promptfoo, Giskard
- Productivity tools
- 4 comparison tables for tools
- Getting started recommendations

#### Supporting Documentation

**QUICKSTART.md**
- 30-day hands-on learning path
- Week-by-week breakdown (Foundations → Prompt Engineering → RAG → Fine-tuning)
- Daily tasks with code examples
- Setup instructions for Python, Ollama, essential libraries
- 4 progressive projects: Simple chatbot, Advanced chatbot, Document Q&A, Production app
- Progress checklist with 16 milestones
- Common issues & solutions
- 3 career paths after completion

**FAQ.md**
- Comprehensive Q&A covering 50+ questions
- 8 major sections:
  - Getting Started (prerequisites, GPU needs, free resources)
  - Models & Architecture (GPT vs BERT, model selection, parameters)
  - Training & Fine-Tuning (RAG vs fine-tuning, costs, LoRA/QLoRA)
  - Prompting & Usage (techniques, hallucinations, parameters)
  - RAG & Applications (vector DBs, chunking, accuracy)
  - Deployment & Production (options, servers, costs)
  - Costs & Resources (free options, GPU requirements)
  - Career & Learning (timeline, jobs, paths)
  - Troubleshooting (CUDA, output quality, performance)
- Decision tables and actionable advice

**GLOSSARY.md**
- 200+ terms and acronyms
- Alphabetically organized A-Z
- Common acronyms quick reference table
- Model families quick reference
- Cross-references to category READMEs
- Related to FAQ and QUICKSTART

#### Updated Files
- **README.md**: Added links to new categories (10-11) and supporting docs (QUICKSTART, FAQ, GLOSSARY)
- **CHANGELOG.md**: Documented v2.4.0 additions

#### Summary of v2.4.0
- **2 new comprehensive categories** (Benchmarks, Tools)
- **3 essential supporting documents** (QUICKSTART, FAQ, GLOSSARY)
- **600+ lines of practical guidance** for beginners
- **9 new comparison tables** for benchmarks and tools
- **30-day actionable learning path** with projects
- **50+ FAQs answered** covering all aspects
- **200+ terms defined** in glossary

---

## [2.3.0] - 2025-10-30

### 🎨 Completed Metadata Enhancement Across ALL Categories

#### Enhanced Remaining Categories (04, 06-09)
- **04-Data-Training**:
  - Added dataset comparison tables (pre-training, instruction, code datasets)
  - Training frameworks comparison (DeepSpeed vs Megatron vs Accelerate)
  - 4-phase learning path for data preparation
  - Key considerations for dataset selection and licensing
  
- **06-Deployment-Ops**:
  - Inference server performance comparison (vLLM vs TGI vs llama.cpp)
  - Quantization methods comparison (FP16 vs INT8 vs GPTQ vs AWQ)
  - Cloud platform comparison (AWS vs GCP vs Azure vs RunPod)
  - 4-phase deployment strategy (Development → MVP → Production → Enterprise)
  - Cost optimization tips and monitoring essentials
  
- **07-Applications**:
  - RAG architecture patterns comparison (Naive vs Advanced vs Modular)
  - Agent patterns comparison (ReAct vs Plan-and-Execute vs Reflexion)
  - Prompt techniques comparison (Zero-shot vs Few-shot vs CoT)
  - 8-week implementation roadmap
  - Best practices for RAG optimization and agent reliability
  
- **08-Advanced-Topics**:
  - Added legend for research maturity levels
  - Categorized by production readiness
  
- **09-Learning-Resources**:
  - University courses comparison (duration, prerequisites, focus)
  - Online courses comparison with certificate availability
  - YouTube channels comparison by content type
  - Books comparison (level, pages, free versions)
  - 3 complete learning paths: Beginner→LLM Engineer (6-12mo), ML Engineer→LLM Specialist (3-6mo), Researcher→LLM Research
  - Staying updated guide (daily/weekly/monthly/quarterly)
  - Learning tips for all levels

#### Summary of v2.3.0 Additions
- **15+ new comparison tables** across categories 04, 06-09
- **5 comprehensive learning paths** with timeline estimates
- **Architecture decision guides** (RAG vs Fine-tuning, Vector DB selection, Chunking strategies)
- **Best practices sections** for production deployment
- **Cost optimization strategies** and monitoring essentials
- **Staying updated guides** with resource recommendations

---

## [2.2.0] - 2025-10-30

### 🎨 Enhanced with Rich Metadata & Comparison Tables

#### Added - Metadata Enhancements
- **Difficulty badges** on all resources:
  - 🟢 Beginner - No prerequisites required
  - 🟡 Intermediate - Basic knowledge recommended
  - 🔴 Advanced - Strong foundation required
- **Time estimates** for each resource (reading time, course duration, implementation time)
- **Last updated dates** (October 2025) for freshness verification
- **Hands-on indicators** (🔧) for practical/code resources
- **Prerequisites** listed for advanced resources
- **GitHub stars** for repositories
- **Popular indicators** (⭐) for widely-used tools

#### Added - Comparison Tables
- **Model comparison**: LLaMA 2 vs Mistral vs Mixtral vs Gemma vs Phi-2 (size, context, license, use cases)
- **Fine-tuning methods**: Full FT vs LoRA vs QLoRA vs Prefix Tuning (memory, speed, parameters)
- **Benchmark scores**: MMLU, HumanEval, GSM8K, TruthfulQA across major models
- **Application frameworks**: LangChain vs LlamaIndex vs Haystack vs Semantic Kernel
- **Deployment frameworks**: vLLM vs TGI vs Ollama vs llama.cpp vs LM Studio
- **Vector databases**: Chroma vs Qdrant vs Weaviate vs Milvus vs Pinecone vs FAISS
- **Agent frameworks**: AutoGPT vs BabyAGI vs CrewAI vs LangGraph vs MetaGPT
- **Tokenizer comparison**: tiktoken vs SentencePiece vs HF Tokenizers vs WordPiece

#### Added - Learning Paths
- **Structured progression** from beginner to advanced for each category
- **Week-by-week schedules** for 4-8 week learning plans
- **Phase-based learning** with clear milestones
- **Paper reading lists** with priority ordering
- **Quick selection guides** (e.g., "Choose LangChain if...", "Choose Ollama if...")

#### Added - Key Takeaways Sections
- **Model selection guidelines** (7B vs 70B, when to use MoE)
- **Fine-tuning strategy recommendations** (QLoRA vs LoRA vs Full FT)
- **Evaluation best practices** (multiple benchmarks, real-world testing)
- **Framework selection criteria** (production vs development, scale considerations)

#### Enhanced Categories
- **01-Fundamentals**: Added legend, TOC, learning paths for 3 learner types
- **02-NLP-Basics**: Added tokenizer comparison table, paper reading list
- **03-Core-LLMs**: Added model comparison, benchmark scores, selection guidelines
- **05-Frameworks**: Added 4 comparison tables, quick selection guide, 8-week learning path

#### Changed
- Main README updated with "What's New" section
- Curation rules expanded to include metadata requirements
- "About" section updated to highlight new features

---

## [2.1.0] - 2025-10-30

### ✨ Added Case Studies

#### Added
- **Case Studies directory** with 100+ real-world LLM implementations
- Organized by 15+ domains: Healthcare, Finance, Legal, E-Commerce, Education, Software Development, Media, Customer Support, Transportation, Gaming, Manufacturing, Government, Research, Business Intelligence, Hospitality, Pharmaceutical, Marketing, Cybersecurity
- ROI and impact studies included
- Success factors and common challenges documented

---

## [2.0.0] - 2025-10-30

### 🚀 Major Restructure - Curation-Only Format

#### Changed
- **Complete repository restructure** from tutorial-style to pure curation format
- **New 9-category organization**:
  - 01-Fundamentals (Python, ML, Deep Learning, Math)
  - 02-NLP-Basics (Tokenization, Embeddings, Transformers)
  - 03-Core-LLMs (Architectures, Fine-tuning, Evaluation)
  - 04-Data-Training (Datasets, Data Prep, Training)
  - 05-Frameworks (Hugging Face, LangChain, Ollama, etc.)
  - 06-Deployment-Ops (Serving, Optimization, Monitoring)
  - 07-Applications (RAG, Agents, Chatbots)
  - 08-Advanced-Topics (RLHF, Alignment, Multimodal, Safety)
  - 09-Learning-Resources (Courses, Papers, Books, Blogs)

#### Removed
- Old directory structure (Tutorials, Research-Papers, Datasets, etc.)
- Tutorial-style content and explanations
- Enhancement planning documents (now obsolete)

#### Added
- 700+ curated free/open-source resources
- Strict curation format: URL, Type, 1-2 line factual note only
- Clear contribution guidelines for curation

---

## [1.0.0] - 2025-10-29

### 🎉 Initial Release

#### Added
- **Main README.md** with comprehensive project overview and navigation
- **Tutorials/** - Tiered learning paths
  - Beginner tutorials covering LLM fundamentals
  - Intermediate tutorials on fine-tuning, RAG, and optimization
  - Advanced tutorials on RLHF, MoE, and cutting-edge research
- **Research-Papers/** - Curated academic papers
  - Model Architecture papers (Transformer, BERT, GPT, etc.)
  - Training Techniques papers (scaling laws, distributed training)
  - Evaluation papers (benchmarks, metrics, safety)
- **Datasets/** - Comprehensive dataset catalog
  - Pre-training datasets (The Pile, C4, RedPajama, etc.)
  - Instruction tuning datasets (Alpaca, Dolly, FLAN)
  - Benchmark datasets (MMLU, HellaSwag, HumanEval)
  - Domain-specific datasets
- **Tools-and-Libraries/** - Complete tool ecosystem
  - Model libraries (Transformers, PEFT)
  - Training frameworks (DeepSpeed, Megatron)
  - Inference engines (vLLM, TGI, llama.cpp)
  - Application frameworks (LangChain, LlamaIndex)
  - Vector databases and evaluation tools
- **Fine-Tuning/** - Complete fine-tuning guide
  - When to fine-tune vs. prompt
  - Methods (LoRA, QLoRA, full fine-tuning)
  - Data preparation best practices
  - Evaluation strategies
- **Prompt-Engineering/** - Comprehensive prompting guide
  - Basic techniques (few-shot, zero-shot, role assignment)
  - Advanced techniques (CoT, ReAct, Tree of Thoughts)
  - Domain-specific templates
  - Best practices and common pitfalls
- **Deployment/** - Production deployment strategies
  - Self-hosted solutions (Ollama, vLLM, TGI)
  - Cloud platforms (AWS, GCP, Azure, Hugging Face)
  - Inference optimization techniques
  - Cost optimization strategies
  - Security and monitoring
- **Ethics-and-Safety/** - Responsible AI guidelines
  - Core ethical principles
  - Bias mitigation strategies
  - Privacy and security considerations
  - Safety implementation patterns
  - Compliance frameworks
- **Case-Studies/** - Real-world implementations
  - Enterprise applications (customer support, code generation)
  - Industry-specific uses (healthcare, finance, legal)
  - Success patterns and failure modes
  - Lessons learned
- **Visualizations/** - Visual learning resources
  - Architecture diagrams and comparisons
  - Concept maps and flowcharts
  - Performance visualizations
  - Interactive tool recommendations
- **Community-Resources/** - Community connections
  - Online communities (Reddit, Discord, forums)
  - Newsletters and blogs
  - YouTube channels and podcasts
  - Twitter/X accounts to follow
  - Conferences and events
  - Research groups
- **LICENSE** - MIT License with attribution guidelines
- **CHANGELOG.md** - This file
- **CONTRIBUTORS.md** - Contributor recognition

#### Repository Features
- 📚 100% free and open-source resources
- 🎓 Tiered content for all skill levels (beginner to advanced)
- 🔗 1000+ curated links to papers, tools, and resources
- ✅ No coding implementations (knowledge-focused)
- 🌍 Community-driven and contribution-friendly
- 📊 Visual learning aids and diagrams
- 🔒 Ethics and safety first approach
- 📖 Clear documentation and navigation

---

## [Unreleased]

### Planned Additions
- [ ] Video tutorial playlists with summaries
- [ ] Interactive learning notebooks (knowledge-focused)
- [ ] Monthly research paper summaries
- [ ] LLM comparison charts and benchmarks
- [ ] Interview preparation guides for LLM roles
- [ ] Career pathways in LLM engineering
- [ ] Hands-on project ideas (without implementations)
- [ ] Troubleshooting guides
- [ ] Glossary of LLM terminology
- [ ] FAQ section
- [ ] Multilingual translations (Spanish, Chinese, etc.)

### Future Enhancements
- Regular updates with latest research papers
- Expanded case studies from various industries
- More domain-specific resources (legal, medical, finance)
- Enhanced visualization resources
- Community spotlight features
- Expert interviews and insights
- Curated learning paths for specific roles
- Resource quality ratings and reviews

---

## Contributing

See [CONTRIBUTING.md](./README.md#contributing) for guidelines on how to contribute to this project.

---

## Links

- **Repository**: https://github.com/VenkataAnilKumar/LLM-Engineering
- **Issues**: https://github.com/VenkataAnilKumar/LLM-Engineering/issues
- **Discussions**: https://github.com/VenkataAnilKumar/LLM-Engineering/discussions

---

*This changelog follows the principles of [Keep a Changelog](https://keepachangelog.com/).*
