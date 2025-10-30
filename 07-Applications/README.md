# 💼 Applications

RAG, Agents, Chatbots, Tool Use, Real-world implementations.

## 📊 Legend

- 🟢 **Beginner** - Easy to implement
- 🟡 **Intermediate** - Moderate complexity
- 🔴 **Advanced** - Complex setup/architecture
- ⏱️ **Implementation Time** - Est. time to build
- 📅 **Updated** - Last verified
- 🔧 **Production-Ready** - Battle-tested
- 🎯 **Use Case** - Primary application

---

## 🔍 RAG (Retrieval-Augmented Generation)

### RAG Paper
- **URL:** https://arxiv.org/abs/2005.11401
- **Title:** Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks
- **Authors:** Lewis et al. (Meta AI)
- **Year:** 2020
- **Note:** Original RAG paper combining retrieval with generation.

### LlamaIndex (GPT Index)
- **URL:** https://github.com/run-llama/llama_index
- **Type:** Framework
- **License:** MIT
- **Note:** Data framework for RAG applications with indexing.

### LangChain
- **URL:** https://github.com/langchain-ai/langchain
- **Type:** Framework
- **License:** MIT
- **Note:** RAG chains, document loaders, vector store integrations.

### Haystack
- **URL:** https://github.com/deepset-ai/haystack
- **Type:** Framework
- **License:** Apache 2.0
- **Note:** NLP framework with RAG pipelines and document search.

### txtai
- **URL:** https://github.com/neuml/txtai
- **Type:** Framework
- **License:** Apache 2.0
- **Note:** Semantic search and RAG pipelines.

### RAGatouille
- **URL:** https://github.com/bclavie/RAGatouille
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Simplified RAG with ColBERT reranking.

---

## 🤖 Agent Frameworks

### AutoGPT
- **URL:** https://github.com/Significant-Gravitas/AutoGPT
- **Type:** Agent Framework
- **License:** MIT
- **Note:** Autonomous GPT-4 agent with memory and web browsing.

### BabyAGI
- **URL:** https://github.com/yoheinakajima/babyagi
- **Type:** Agent Framework
- **License:** MIT
- **Note:** Task-driven autonomous agent with task management.

### AgentGPT
- **URL:** https://github.com/reworkd/AgentGPT
- **Type:** Agent Platform
- **License:** GPL-3.0
- **Note:** Browser-based autonomous AI agent platform.

### LangGraph
- **URL:** https://github.com/langchain-ai/langgraph
- **Type:** Framework
- **Maintainer:** LangChain
- **License:** MIT
- **Note:** Build cyclic agent workflows with state persistence.

### CrewAI
- **URL:** https://github.com/joaomdmoura/crewai
- **Type:** Framework
- **License:** MIT
- **Note:** Orchestrate role-playing autonomous agents.

### Agents by LlamaIndex
- **URL:** https://docs.llamaindex.ai/en/stable/use_cases/agents.html
- **Type:** Documentation + Framework
- **Note:** ReAct agents with tool use.

---

## 🛠️ Tool Use & Function Calling

### Toolformer Paper
- **URL:** https://arxiv.org/abs/2302.04761
- **Title:** Toolformer: Language Models Can Teach Themselves to Use Tools
- **Authors:** Schick et al. (Meta AI)
- **Year:** 2023
- **Note:** LLMs learning to use external tools.

### Gorilla: Large Language Model Connected with Massive APIs
- **URL:** https://arxiv.org/abs/2305.15334
- **Type:** Paper + Model
- **Year:** 2023
- **Note:** Fine-tuned LLaMA for API calls.

### ToolLLM
- **URL:** https://github.com/OpenBMB/ToolBench
- **Type:** Framework + Dataset
- **License:** Apache 2.0
- **Note:** Tool learning and benchmarking for LLMs.

### OpenAI Function Calling
- **URL:** https://platform.openai.com/docs/guides/function-calling
- **Type:** Documentation
- **Note:** Official OpenAI function calling guide.

---

## 💬 Chatbot Templates

### Chainlit
- **URL:** https://github.com/Chainlit/chainlit
- **Type:** UI Framework
- **License:** Apache 2.0
- **Note:** Build conversational AI interfaces quickly.

### Streamlit Chat
- **URL:** https://docs.streamlit.io/library/api-reference/chat
- **Type:** UI Component
- **Note:** Chat interface components for Streamlit apps.

### Gradio Chatbot
- **URL:** https://www.gradio.app/docs/chatbot
- **Type:** UI Component
- **Note:** Chatbot interface for Gradio apps.

### Text Generation WebUI
- **URL:** https://github.com/oobabooga/text-generation-webui
- **Type:** Web Interface
- **License:** AGPL-3.0
- **Note:** Feature-rich chatbot UI for local models.

### Open WebUI (Formerly Ollama WebUI)
- **URL:** https://github.com/open-webui/open-webui
- **Type:** Web Interface
- **License:** MIT
- **Note:** ChatGPT-style interface for local LLMs.

---

## 📝 Prompt Engineering Patterns

### ReAct: Synergizing Reasoning and Acting
- **URL:** https://arxiv.org/abs/2210.03629
- **Title:** ReAct: Synergizing Reasoning and Acting in Language Models
- **Year:** 2022
- **Note:** Interleaving reasoning traces with actions.

### Chain-of-Thought Prompting
- **URL:** https://arxiv.org/abs/2201.11903
- **Title:** Chain-of-Thought Prompting Elicits Reasoning
- **Authors:** Wei et al. (Google)
- **Year:** 2022
- **Note:** Step-by-step reasoning improves performance.

### Tree of Thoughts
- **URL:** https://arxiv.org/abs/2305.10601
- **Title:** Tree of Thoughts: Deliberate Problem Solving
- **Year:** 2023
- **Note:** Explore multiple reasoning paths.

### Self-Consistency
- **URL:** https://arxiv.org/abs/2203.11171
- **Title:** Self-Consistency Improves Chain of Thought Reasoning
- **Year:** 2022
- **Note:** Sample multiple reasoning paths, select majority.

### DSPy: Programming with Foundation Models
- **URL:** https://github.com/stanfordnlp/dspy
- **Type:** Framework
- **License:** MIT
- **Note:** Programmatic prompt optimization framework.

---

## 📚 Document Processing

### Unstructured
- **URL:** https://github.com/Unstructured-IO/unstructured
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Parse unstructured documents (PDF, HTML, Word, etc.).

### LangChain Document Loaders
- **URL:** https://python.langchain.com/docs/modules/data_connection/document_loaders/
- **Type:** Documentation
- **Note:** 100+ document loaders for various formats.

### PyPDF2 / PyMuPDF
- **URL:** https://github.com/pymupdf/PyMuPDF
- **Type:** Library
- **License:** AGPL / Commercial
- **Note:** PDF parsing and extraction.

### Docling
- **URL:** https://github.com/DS4SD/docling
- **Type:** Library
- **Maintainer:** IBM Research
- **License:** MIT
- **Note:** Document understanding and conversion.

---

## 🎯 Semantic Search

### Sentence Transformers
- **URL:** https://github.com/UKPLab/sentence-transformers
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Compute sentence embeddings for semantic search.

### ColBERT: Efficient and Effective Passage Search
- **URL:** https://github.com/stanford-futuredata/ColBERT
- **Type:** Framework
- **License:** MIT
- **Note:** Late interaction retrieval model.

### BGE Embeddings
- **URL:** https://huggingface.co/BAAI/bge-large-en-v1.5
- **Type:** Model
- **Note:** State-of-the-art open embedding models.

### E5 Embeddings
- **URL:** https://huggingface.co/intfloat/e5-large-v2
- **Type:** Model
- **Note:** Text embeddings from Microsoft.

---

## 🔗 Integration Examples

### LangChain Templates
- **URL:** https://github.com/langchain-ai/langchain/tree/master/templates
- **Type:** Code Templates
- **Note:** Pre-built application templates (RAG, agents, etc.).

### LlamaIndex Examples
- **URL:** https://github.com/run-llama/llama_index/tree/main/docs/examples
- **Type:** Code Examples
- **Note:** Notebooks demonstrating various use cases.

### Vercel AI SDK
- **URL:** https://github.com/vercel/ai
- **Type:** SDK
- **License:** Apache 2.0
- **Note:** Build AI-powered apps with React/Vue/Svelte.

---

## 💼 Real-World Implementations

### Quivr: Your Second Brain
- **URL:** https://github.com/QuivrHQ/quivr
- **Type:** Application
- **License:** Apache 2.0
- **Note:** RAG-based personal knowledge assistant.

### Danswer
- **URL:** https://github.com/danswer-ai/danswer
- **Type:** Application
- **License:** MIT
- **Note:** Enterprise search with LLMs and connectors.

### PrivateGPT
- **URL:** https://github.com/imartinez/privateGPT
- **Type:** Application
- **License:** Apache 2.0
- **Note:** Private document Q&A with local LLMs.

### LocalGPT
- **URL:** https://github.com/PromtEngineer/localGPT
- **Type:** Application
- **License:** Apache 2.0
- **Note:** Chat with documents locally using RAG.

---

## 📊 Evaluation for Applications

### RAGAS: RAG Assessment
- **URL:** https://github.com/explodinggradients/ragas
- **Type:** Library
- **License:** Apache 2.0
- **Note:** Evaluation metrics for RAG systems.

### TruLens
- **URL:** https://github.com/truera/trulens
- **Type:** Evaluation Framework
- **License:** MIT
- **Note:** Evaluate and track LLM applications.

---

## 📚 Learning Resources

### Building LLM Applications
- **URL:** https://www.deeplearning.ai/short-courses/
- **Type:** Course Series
- **Provider:** DeepLearning.AI
- **Note:** Free courses on LangChain, vector databases, RAG.

### Full Stack LLM Bootcamp
- **URL:** https://fullstackdeeplearning.com/llm-bootcamp/
- **Type:** Course Materials
- **Note:** Building production LLM applications.

### LangChain Documentation
- **URL:** https://python.langchain.com/docs/
- **Type:** Documentation
- **Note:** Comprehensive guide to building LLM apps.

### LlamaIndex Documentation
- 🟢 Beginner | ⏱️ 10 hours | 📅 Oct 2025
- **URL:** https://docs.llamaindex.ai/
- **Type:** Documentation
- **Note:** Complete guide to RAG and data frameworks.

---

## 🔀 Application Patterns Comparison

### RAG Architecture Patterns

| Pattern | Complexity | Accuracy | Cost | Use Case |
|---------|------------|----------|------|----------|
| **Naive RAG** | 🟢 Simple | ⭐⭐⭐ Good | 💰 Low | Basic Q&A, documentation |
| **Advanced RAG** | 🟡 Moderate | ⭐⭐⭐⭐ High | 💰💰 Medium | Production chatbots |
| **Modular RAG** | 🔴 Complex | ⭐⭐⭐⭐⭐ Excellent | 💰💰💰 High | Enterprise systems |
| **Agentic RAG** | 🔴 Complex | ⭐⭐⭐⭐⭐ Excellent | 💰💰💰 High | Complex reasoning |
| **GraphRAG** | 🔴 Complex | ⭐⭐⭐⭐⭐ Excellent | 💰💰💰 High | Relationship queries |

### Agent Patterns

| Pattern | Autonomy | Tool Use | Reliability | Best For |
|---------|----------|----------|-------------|----------|
| **ReAct** | 🤖🤖 Medium | ✅ Yes | ⭐⭐⭐⭐ High | Tool-using tasks |
| **Plan-and-Execute** | 🤖🤖🤖 High | ✅ Yes | ⭐⭐⭐ Good | Multi-step tasks |
| **ReWOO** | 🤖🤖 Medium | ✅ Yes | ⭐⭐⭐⭐ High | Efficient reasoning |
| **Reflexion** | 🤖🤖🤖 High | ✅ Yes | ⭐⭐⭐⭐⭐ Excellent | Self-improvement |
| **AutoGPT-style** | 🤖🤖🤖🤖 Very High | ✅ Yes | ⭐⭐ Moderate | Autonomous tasks |

### Prompt Techniques

| Technique | Complexity | Performance Gain | Token Cost | When to Use |
|-----------|------------|------------------|------------|-------------|
| **Zero-shot** | 🟢 Simple | Baseline | 💰 Low | Simple tasks |
| **Few-shot** | 🟢 Simple | +20% | 💰💰 Medium | Pattern learning |
| **Chain-of-Thought** | 🟡 Moderate | +30% | 💰💰 Medium | Reasoning tasks |
| **Tree-of-Thoughts** | 🔴 Complex | +40% | 💰💰💰 High | Complex reasoning |
| **ReAct** | 🟡 Moderate | +35% | 💰💰 Medium | Tool-using |
| **Self-Consistency** | 🟡 Moderate | +25% | 💰💰💰 High | High-stakes tasks |

### Chatbot Types

| Type | Complexity | Capabilities | Memory | Best Use |
|------|------------|--------------|--------|----------|
| **Stateless Bot** | 🟢 Simple | Basic Q&A | None | FAQ, simple queries |
| **Session-based** | 🟡 Moderate | Context tracking | Short-term | Customer support |
| **Memory-enabled** | 🔴 Complex | Personalization | Long-term | Personal assistant |
| **Multi-agent** | 🔴 Complex | Specialized tasks | Shared | Enterprise workflows |

---

## 🎓 Implementation Roadmap

### Week 1-2: RAG Fundamentals
**Build**: Basic RAG chatbot
1. Choose framework (LlamaIndex recommended for beginners)
2. Set up vector database (Chroma locally)
3. Implement document loading and chunking
4. Create simple Q&A interface
**Time**: 10-15 hours

### Week 3-4: Advanced RAG
**Build**: Production-ready RAG
1. Add reranking (ColBERT via RAGatouille)
2. Implement hybrid search (BM25 + vector)
3. Add query transformation
4. Implement caching and monitoring
**Time**: 15-20 hours

### Week 5-6: Agent Systems
**Build**: Tool-using agent
1. Implement ReAct pattern
2. Add function calling/tools
3. Create error handling
4. Test with multiple tools
**Time**: 20-25 hours

### Week 7-8: Production Polish
**Build**: Deployed application
1. Add evaluation metrics
2. Implement logging and observability
3. Create user feedback loop
4. Deploy with proper security
**Time**: 15-20 hours

---

## 🔑 Architecture Decisions

### RAG vs Fine-tuning?
**Use RAG when:**
- Data changes frequently
- Need source attribution
- Limited training resources
- Domain knowledge in documents

**Use Fine-tuning when:**
- Need specific tone/style
- Fixed knowledge base
- Have quality training data
- Budget for training

**Use Both when:**
- Complex domain requirements
- Need both style and knowledge
- Production applications

### Vector Database Selection
**Chroma** → Development, prototyping
**Qdrant** → Production, complex filtering
**Pinecone** → Managed service, easy scaling
**Weaviate** → Multi-modal, graph features
**FAISS** → Research, maximum performance

### Chunking Strategies
- **Fixed-size (512 tokens)**: Simple, consistent
- **Semantic**: Better context, more complex
- **Recursive**: Good for code, hierarchical docs
- **Overlap (50-100 tokens)**: Reduces context breaks

---

## 💡 Best Practices

**RAG Optimization:**
1. **Chunking**: Test different sizes (256-1024 tokens)
2. **Retrieval**: Use hybrid search (keyword + semantic)
3. **Reranking**: Add ColBERT or cross-encoder
4. **Query**: Implement HyDE (hypothetical document embeddings)
5. **Context**: Use parent document retrieval

**Agent Reliability:**
1. **Error Handling**: Implement retries with exponential backoff
2. **Validation**: Verify tool outputs before using
3. **Limits**: Set max iterations and timeouts
4. **Logging**: Track all agent decisions
5. **Human-in-loop**: Allow human override for critical tasks

**Production Checklist:**
- ✅ Rate limiting
- ✅ Caching (semantic cache for similar queries)
- ✅ Monitoring (latency, accuracy, cost)
- ✅ Feedback collection
- ✅ A/B testing framework
- ✅ Fallback mechanisms
- ✅ Security (input validation, output filtering)

---

**Last Updated:** October 2025
