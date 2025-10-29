# 🎓 Intermediate Tutorials

Welcome to **Intermediate LLM Engineering**! This section builds on foundational knowledge and dives deeper into practical applications, optimization techniques, and advanced concepts.

---

## 🎯 Learning Objectives

By completing these tutorials, you will:
- ✅ Master advanced prompt engineering techniques
- ✅ Understand fine-tuning and transfer learning
- ✅ Learn model optimization and efficiency techniques
- ✅ Explore retrieval-augmented generation (RAG)
- ✅ Understand evaluation metrics and benchmarking
- ✅ Learn about different model architectures
- ✅ Gain practical experience with LLM frameworks

---

## 📖 Table of Contents

1. [Advanced Prompt Engineering](#1-advanced-prompt-engineering)
2. [Fine-Tuning Fundamentals](#2-fine-tuning-fundamentals)
3. [Retrieval-Augmented Generation (RAG)](#3-retrieval-augmented-generation-rag)
4. [Model Evaluation & Benchmarking](#4-model-evaluation--benchmarking)
5. [Model Architectures Comparison](#5-model-architectures-comparison)
6. [Optimization Techniques](#6-optimization-techniques)
7. [Working with Different Modalities](#7-working-with-different-modalities)
8. [LLM Frameworks & APIs](#8-llm-frameworks--apis)
9. [Next Steps](#9-next-steps)

---

## 1. Advanced Prompt Engineering

### 🎓 Free Learning Resources

#### Comprehensive Guides
- **[Prompt Engineering Guide - Advanced Techniques](https://www.promptingguide.ai/techniques)** ⭐
  - Chain-of-Thought (CoT)
  - Tree of Thoughts
  - ReAct framework
  - Self-Consistency

- **[OpenAI Cookbook](https://cookbook.openai.com/)** ⭐
  - Production-ready examples
  - Best practices
  - Code snippets (for understanding concepts)

#### Advanced Techniques

**1. Chain-of-Thought (CoT) Prompting**
```
Problem: What is 23 * 47?

Prompt: "Let's solve this step by step:
1. Break down: 23 * 47 = 23 * (40 + 7)
2. Calculate: 23 * 40 = 920
3. Calculate: 23 * 7 = 161
4. Add: 920 + 161 = 1,081"
```

**2. Few-Shot with CoT**
```
Q: Roger has 5 tennis balls. He buys 2 more cans of 3. How many does he have?
A: Roger started with 5 balls. 2 cans of 3 is 6. 5 + 6 = 11. Answer: 11

Q: The cafeteria had 23 apples. They used 20 for lunch and bought 6 more. How many do they have?
A: [Let model complete with reasoning]
```

**3. Self-Consistency**
- Generate multiple reasoning paths
- Use majority voting
- Improves accuracy on complex tasks

**4. ReAct (Reasoning + Acting)**
```
Thought: I need to find the population of Tokyo
Action: Search[Tokyo population]
Observation: Tokyo has approximately 14 million people
Thought: Now I have the information needed
Answer: Tokyo's population is approximately 14 million
```

#### Video Tutorials
- **[Advanced Prompt Engineering](https://www.youtube.com/watch?v=H4YK_7MAckk)** by AI Explained
- **[Chain-of-Thought Prompting](https://www.youtube.com/watch?v=H0DHBdJQRfE)** by Yannic Kilcher

#### Research Papers (Explained)
- **[Chain-of-Thought Prompting](https://arxiv.org/abs/2201.11903)** - Wei et al., 2022
- **[ReAct: Reasoning and Acting](https://arxiv.org/abs/2210.03629)** - Yao et al., 2022
- **[Tree of Thoughts](https://arxiv.org/abs/2305.10601)** - Yao et al., 2023

### 💡 Practice Exercises

1. Create a multi-step reasoning prompt for a complex problem
2. Implement few-shot learning for a classification task
3. Design a ReAct-style prompt for information retrieval
4. Compare zero-shot vs. few-shot performance

---

## 2. Fine-Tuning Fundamentals

### 🎓 Free Learning Resources

#### Comprehensive Guides
- **[Hugging Face Fine-Tuning Tutorial](https://huggingface.co/learn/nlp-course/chapter3/1)** ⭐
  - Complete fine-tuning guide
  - Practical examples
  - Best practices

- **[OpenAI Fine-Tuning Guide](https://platform.openai.com/docs/guides/fine-tuning)**
  - When to fine-tune
  - Data preparation
  - Evaluation strategies

#### Key Concepts

**When to Fine-Tune**
- ✅ Need consistent behavior/format
- ✅ Domain-specific knowledge required
- ✅ Have quality training data (500+ examples)
- ✅ Prompting doesn't achieve desired results
- ❌ Don't have enough data
- ❌ Problem can be solved with prompting
- ❌ Don't have evaluation metrics

**Types of Fine-Tuning**
1. **Full Fine-Tuning**: Update all model parameters
2. **Parameter-Efficient Fine-Tuning (PEFT)**:
   - LoRA (Low-Rank Adaptation)
   - Prefix Tuning
   - Adapter Layers
   - QLoRA (Quantized LoRA)

**Data Preparation**
```
Format: Instruction → Response pairs
Quality: High-quality, diverse examples
Quantity: 500-10,000+ examples recommended
Balance: Representative of use cases
```

#### Tutorials
- **[Fine-Tune LLaMA](https://www.philschmid.de/fine-tune-flan-t5)** by Philipp Schmid
- **[LoRA Explained](https://huggingface.co/blog/lora)** by Hugging Face
- **[PEFT Library Guide](https://huggingface.co/docs/peft/index)**

#### Video Resources
- **[Fine-Tuning Large Language Models](https://www.youtube.com/watch?v=eC6Hd1hFvos)** by Shaw Talebi
- **[LoRA: Low-Rank Adaptation](https://www.youtube.com/watch?v=DhRoTONcyZE)** by Efficient NLP

### 🔑 Best Practices

1. **Start with prompting** - Only fine-tune if necessary
2. **Use PEFT methods** - More efficient than full fine-tuning
3. **Prepare quality data** - Garbage in, garbage out
4. **Evaluate systematically** - Use held-out test sets
5. **Monitor for overfitting** - Don't train too long

---

## 3. Retrieval-Augmented Generation (RAG)

### 🎓 Free Learning Resources

#### What is RAG?

RAG combines LLMs with external knowledge retrieval to provide accurate, up-to-date information. Think of it as giving the LLM access to a search engine or database.

**Architecture**:
```
User Query → Retrieve Relevant Docs → Augment Prompt → LLM → Response
```

#### Comprehensive Guides
- **[RAG Tutorial by LangChain](https://python.langchain.com/docs/use_cases/question_answering/)** ⭐
  - Complete implementation guide
  - Best practices
  - Multiple approaches

- **[Building RAG Systems](https://www.pinecone.io/learn/retrieval-augmented-generation/)** by Pinecone ⭐
  - Conceptual overview
  - Architecture patterns
  - Optimization tips

- **[LlamaIndex Documentation](https://docs.llamaindex.ai/)** ⭐
  - RAG framework
  - Multiple data sources
  - Advanced techniques

#### Key Components

**1. Document Loading & Chunking**
- Split documents into manageable pieces
- Preserve context
- Optimal chunk size: 256-512 tokens

**2. Embedding Generation**
- Convert text to vectors
- Free models: sentence-transformers
- Popular: all-MiniLM-L6-v2

**3. Vector Storage**
- Store and index embeddings
- Free options: FAISS, ChromaDB
- Cloud: Pinecone (free tier), Weaviate

**4. Retrieval Strategy**
- Semantic search
- Hybrid search (semantic + keyword)
- Re-ranking

**5. Prompt Augmentation**
```
Context: [Retrieved Documents]
Question: [User Query]
Answer based on the context above:
```

#### Free Tools for RAG
- **[LangChain](https://www.langchain.com/)** - RAG framework
- **[LlamaIndex](https://www.llamaindex.ai/)** - Data framework for LLMs
- **[ChromaDB](https://www.trychroma.com/)** - Vector database
- **[FAISS](https://github.com/facebookresearch/faiss)** - Facebook's similarity search
- **[Haystack](https://haystack.deepset.ai/)** - NLP framework

#### Video Tutorials
- **[RAG Explained](https://www.youtube.com/watch?v=T-D1OfcDW1M)** by LangChain
- **[Building RAG Systems](https://www.youtube.com/watch?v=sVcwVQRHIc8)** by DeepLearning.AI

#### Advanced RAG Techniques
- **Multi-query retrieval**
- **Hypothetical document embedding**
- **Re-ranking with cross-encoders**
- **Hierarchical retrieval**

### 💡 Practice Projects

1. Build a personal document Q&A system
2. Create a knowledge base chatbot
3. Implement semantic search over PDFs
4. Compare different retrieval strategies

---

## 4. Model Evaluation & Benchmarking

### 🎓 Free Learning Resources

#### Why Evaluation Matters

- Measure model performance objectively
- Compare different models or approaches
- Track improvements over time
- Identify weaknesses and biases

#### Common Benchmarks

**General Language Understanding**
- **GLUE** (General Language Understanding Evaluation)
- **SuperGLUE** (More challenging version)
- **MMLU** (Massive Multitask Language Understanding)

**Reasoning & Knowledge**
- **HellaSwag** - Commonsense reasoning
- **ARC** - Question answering
- **TruthfulQA** - Truthfulness evaluation

**Coding**
- **HumanEval** - Python code generation
- **MBPP** - Python programming problems

**Safety & Bias**
- **ToxiGen** - Toxicity detection
- **BBQ** - Bias benchmark
- **WinoGender** - Gender bias

#### Evaluation Metrics

**Automatic Metrics**
- **Perplexity**: Lower is better (language modeling)
- **BLEU**: Translation quality (0-100)
- **ROUGE**: Summarization quality
- **Exact Match**: Question answering
- **F1 Score**: Classification tasks

**Human Evaluation**
- Fluency
- Coherence
- Relevance
- Factuality
- Safety

#### Resources
- **[HELM Benchmark](https://crfm.stanford.edu/helm/latest/)** by Stanford ⭐
  - Holistic evaluation
  - Multiple scenarios
  - Transparent results

- **[Open LLM Leaderboard](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard)** ⭐
  - Compare open models
  - Multiple benchmarks
  - Community-driven

- **[LM Evaluation Harness](https://github.com/EleutherAI/lm-evaluation-harness)** by EleutherAI
  - Standardized evaluation
  - Multiple tasks
  - Open-source

#### Tutorials
- **[How to Evaluate LLMs](https://www.deeplearning.ai/short-courses/evaluating-debugging-generative-ai/)** by DeepLearning.AI
- **[Evaluation Guide](https://huggingface.co/docs/evaluate/index)** by Hugging Face

### 💡 Key Considerations

- **No single metric is perfect**
- **Context matters** - Choose appropriate benchmarks
- **Human evaluation is gold standard** but expensive
- **Watch for benchmark contamination**
- **Evaluate on your specific use case**

---

## 5. Model Architectures Comparison

### 🎓 Understanding Different Architectures

#### Encoder-Only Models (BERT-style)

**Examples**: BERT, RoBERTa, ALBERT, DeBERTa

**Strengths**:
- ✅ Bidirectional context
- ✅ Great for classification
- ✅ Excellent for embeddings
- ✅ Understanding tasks

**Use Cases**:
- Text classification
- Named entity recognition
- Question answering (extractive)
- Semantic search

**Free Resources**:
- [BERT Explained](https://jalammar.github.io/illustrated-bert/)
- [Hugging Face BERT Course](https://huggingface.co/learn/nlp-course/chapter1/1)

#### Decoder-Only Models (GPT-style)

**Examples**: GPT-2, GPT-3, GPT-4, LLaMA, Mistral

**Strengths**:
- ✅ Excellent for generation
- ✅ Few-shot learning
- ✅ Creative tasks
- ✅ Long-form content

**Use Cases**:
- Text generation
- Chatbots
- Code generation
- Creative writing

**Free Resources**:
- [GPT-2 Illustrated](https://jalammar.github.io/illustrated-gpt2/)
- [Decoder-Only Transformers](https://huggingface.co/blog/how-to-generate)

#### Encoder-Decoder Models (T5-style)

**Examples**: T5, BART, Flan-T5

**Strengths**:
- ✅ Versatile architecture
- ✅ Good for seq2seq tasks
- ✅ Summarization
- ✅ Translation

**Use Cases**:
- Translation
- Summarization
- Question answering
- Text-to-text tasks

**Free Resources**:
- [T5 Understanding](https://huggingface.co/docs/transformers/model_doc/t5)
- [Encoder-Decoder Models](https://huggingface.co/learn/nlp-course/chapter1/7)

#### Comparison Table

| Feature | Encoder-Only | Decoder-Only | Encoder-Decoder |
|---------|-------------|--------------|-----------------|
| **Generation** | ❌ No | ✅ Excellent | ✅ Good |
| **Understanding** | ✅ Excellent | ⚠️ Limited | ✅ Good |
| **Bidirectional** | ✅ Yes | ❌ No | ✅ (Encoder) |
| **Few-Shot** | ❌ Limited | ✅ Excellent | ⚠️ Moderate |
| **Speed** | ⚡ Fast | ⚡ Moderate | ⚡ Slower |

### 🔑 Choosing the Right Architecture

- **Need understanding?** → Encoder-Only
- **Need generation?** → Decoder-Only
- **Need seq2seq?** → Encoder-Decoder
- **Need both?** → Decoder-Only (modern LLMs)

---

## 6. Optimization Techniques

### 🎓 Making LLMs More Efficient

#### Quantization

**What**: Reduce model precision (32-bit → 8-bit/4-bit)
**Benefits**: Less memory, faster inference
**Trade-off**: Slight accuracy loss

**Methods**:
- **8-bit quantization** - Minimal accuracy loss
- **4-bit quantization** - More aggressive
- **GPTQ** - Post-training quantization
- **AWQ** - Activation-aware quantization

**Free Resources**:
- [Quantization Guide](https://huggingface.co/docs/optimum/concept_guides/quantization)
- [bitsandbytes](https://github.com/TimDettmers/bitsandbytes)

#### Pruning

**What**: Remove less important parameters
**Benefits**: Smaller models, faster inference
**Trade-off**: Can reduce capabilities

**Types**:
- Unstructured pruning
- Structured pruning
- Task-specific pruning

#### Knowledge Distillation

**What**: Train smaller "student" model from larger "teacher"
**Benefits**: Maintain performance with smaller size
**Examples**: DistilBERT, TinyBERT

**Free Resources**:
- [Distillation Tutorial](https://huggingface.co/blog/knowledge-distillation)

#### Efficient Attention

**Flash Attention**:
- 2-4x faster
- Less memory usage
- Same results

**Resources**:
- [Flash Attention Paper](https://arxiv.org/abs/2205.14135)
- [Implementation Guide](https://github.com/Dao-AILab/flash-attention)

#### Inference Optimization

**Techniques**:
- **Batching**: Process multiple requests together
- **Caching**: Store common responses
- **Streaming**: Return tokens as generated
- **Speculative Decoding**: Speed up generation

**Tools**:
- [vLLM](https://github.com/vllm-project/vllm) - Fast inference engine
- [Text Generation Inference](https://github.com/huggingface/text-generation-inference)
- [CTranslate2](https://github.com/OpenNMT/CTranslate2)

### 💡 Optimization Strategy

1. **Profile first** - Find bottlenecks
2. **Quantize** - 8-bit for most cases
3. **Optimize attention** - Use Flash Attention
4. **Batch requests** - When possible
5. **Cache results** - For common queries

---

## 7. Working with Different Modalities

### 🎓 Beyond Text

#### Multimodal Models

**Vision-Language Models**
- **CLIP** - Image-text understanding
- **GPT-4 Vision** - Image analysis
- **LLaVA** - Open-source vision LLM
- **Gemini** - Google's multimodal model

**Audio-Language Models**
- **Whisper** - Speech recognition (OpenAI)
- **AudioLM** - Audio generation
- **MusicLM** - Music generation

**Free Resources**:
- [CLIP Tutorial](https://huggingface.co/docs/transformers/model_doc/clip)
- [Whisper Guide](https://github.com/openai/whisper)
- [Multimodal Learning](https://github.com/pliang279/awesome-multimodal-ml)

#### Use Cases

**Vision + Language**:
- Image captioning
- Visual question answering
- OCR and document understanding
- Image generation from text

**Audio + Language**:
- Speech-to-text transcription
- Audio summarization
- Voice assistants
- Music generation

### 💡 Getting Started

1. Start with pre-trained models
2. Use APIs for experimentation
3. Understand modality-specific challenges
4. Consider fine-tuning for specific domains

---

## 8. LLM Frameworks & APIs

### 🛠️ Popular Free Frameworks

#### LangChain
- **Purpose**: Build LLM applications
- **Features**: Chains, agents, memory
- **Best For**: Complex workflows
- **Resources**: [LangChain Docs](https://python.langchain.com/docs/get_started/introduction)

#### LlamaIndex
- **Purpose**: Data framework for LLMs
- **Features**: RAG, indexing, querying
- **Best For**: Knowledge bases
- **Resources**: [LlamaIndex Docs](https://docs.llamaindex.ai/)

#### Hugging Face Transformers
- **Purpose**: Model library
- **Features**: 1000s of models, easy API
- **Best For**: Model experimentation
- **Resources**: [Transformers Docs](https://huggingface.co/docs/transformers/index)

#### Semantic Kernel (Microsoft)
- **Purpose**: AI orchestration
- **Features**: Skills, planning, memory
- **Best For**: Enterprise applications
- **Resources**: [Semantic Kernel](https://github.com/microsoft/semantic-kernel)

### 🌐 Free API Access

**OpenAI**
- Free tier with limits
- $5 credit for new users
- [API Docs](https://platform.openai.com/docs/introduction)

**Hugging Face**
- Free inference API
- Rate limited
- [Inference API](https://huggingface.co/inference-api)

**Google AI Studio**
- Free access to Gemini
- Generous limits
- [AI Studio](https://aistudio.google.com/)

**Anthropic Claude**
- Free tier available
- API and web interface
- [Claude Docs](https://docs.anthropic.com/)

### 💡 Framework Comparison

| Framework | Best For | Learning Curve | Flexibility |
|-----------|----------|----------------|-------------|
| LangChain | Full apps | Moderate | High |
| LlamaIndex | RAG/Search | Easy | Medium |
| Transformers | Models | Easy | Very High |
| Semantic Kernel | Enterprise | Moderate | High |

---

## 9. Next Steps

### ✅ Checklist Before Moving to Advanced

- [ ] Mastered advanced prompt engineering techniques
- [ ] Understood fine-tuning concepts and when to use them
- [ ] Built at least one RAG application
- [ ] Familiar with evaluation metrics and benchmarks
- [ ] Compared different model architectures
- [ ] Explored optimization techniques
- [ ] Experimented with multimodal models
- [ ] Used at least 2 LLM frameworks

### 🚀 Ready for Advanced Topics?

Move on to:
- **[Advanced Tutorials](../Advanced/)** - Cutting-edge techniques
- **[Research Papers](../../Research-Papers/)** - Deep dives
- **[Fine-Tuning](../../Fine-Tuning/)** - Production fine-tuning
- **[Deployment](../../Deployment/)** - Scale your applications

---

## 📚 Recommended Learning Path

### Month 1: Core Concepts
- **Week 1-2**: Advanced prompt engineering
- **Week 3-4**: Fine-tuning fundamentals

### Month 2: Practical Applications
- **Week 1-2**: Build RAG systems
- **Week 3-4**: Model evaluation & optimization

### Month 3: Specialization
- **Week 1-2**: Multimodal models or specific architecture
- **Week 3-4**: Production frameworks & APIs

---

## 🎯 Project Ideas

1. **Personal Knowledge Assistant**
   - RAG over your documents
   - Conversation memory
   - Multi-turn dialogue

2. **Domain-Specific Fine-Tuned Model**
   - Collect training data
   - Fine-tune with PEFT
   - Evaluate systematically

3. **Multi-Agent System**
   - Specialized agents
   - Agent coordination
   - Tool integration

4. **Evaluation Dashboard**
   - Compare models
   - Track performance
   - Visualize results

---

## 💬 Need Help?

- **Questions?** Check [Community Resources](../../Community-Resources/)
- **Projects?** Share in [Case Studies](../../Case-Studies/)
- **Contribute?** See [Contributing Guidelines](../../README.md#contributing)

---

<div align="center">

**Keep Building! 🚀**

[⬅️ Previous: Beginner Tutorials](../Beginner/) | [⬆ Back to Top](#-intermediate-tutorials) | [➡️ Next: Advanced Tutorials](../Advanced/)

</div>
