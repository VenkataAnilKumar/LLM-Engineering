# 🚀 Quick Start Guide

**Get started with LLM Engineering in 30 days** - A practical, hands-on roadmap.

---

## 📋 Prerequisites

Before starting, you should have:
- ✅ **Python 3.8+** installed
- ✅ **Basic programming knowledge** (loops, functions, classes)
- ✅ **Command line familiarity** (cd, ls, pip)
- ✅ **8GB+ RAM** recommended (16GB+ for local models)
- ✅ **GPU optional** but helpful (Colab provides free GPU)

---

## 🎯 30-Day Learning Path

### **Week 1: Foundations** (Days 1-7)
*Goal: Understand what LLMs are and how to use them*

#### Day 1-2: Introduction to LLMs
- 📺 Watch: [Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g) by Andrej Karpathy (1 hour)
- 📖 Read: [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) (30 min)
- 🎯 **Task**: Understand transformer architecture basics

#### Day 3-4: Using Your First LLM
- 🔧 **Setup**:
  ```bash
  pip install openai anthropic
  ```
- 📝 **Try**: ChatGPT API or Claude
  ```python
  import openai
  
  response = openai.ChatCompletion.create(
      model="gpt-3.5-turbo",
      messages=[{"role": "user", "content": "Explain LLMs simply"}]
  )
  print(response.choices[0].message.content)
  ```
- 🎯 **Task**: Make 10 different API calls, experiment with prompts

#### Day 5-7: Local LLM Setup
- 🔧 **Install Ollama**:
  ```bash
  # Mac/Linux
  curl -fsSL https://ollama.ai/install.sh | sh
  
  # Windows
  # Download from https://ollama.ai/download
  
  # Pull a model
  ollama pull llama2:7b
  
  # Run it
  ollama run llama2:7b
  ```
- 🎯 **Task**: Run LLaMA 2 locally, compare with ChatGPT responses

**Week 1 Checkpoint**: ✅ You can use LLMs via API and locally

---

### **Week 2: Prompt Engineering** (Days 8-14)
*Goal: Master effective prompting techniques*

#### Day 8-9: Prompt Basics
- 📖 Read: [Prompt Engineering Guide](https://www.promptingguide.ai/) (2 hours)
- 📝 **Try**: Different prompt patterns:
  ```python
  # Zero-shot
  "Translate to French: Hello, world!"
  
  # Few-shot
  "English: Hello, French: Bonjour\nEnglish: Goodbye, French: Au revoir\nEnglish: Thank you, French:"
  
  # Chain-of-Thought
  "Let's think step by step: What's 23 * 47?"
  ```
- 🎯 **Task**: Create 5 prompts for different tasks

#### Day 10-12: Advanced Prompting
- 🔧 **Install LangChain**:
  ```bash
  pip install langchain langchain-openai
  ```
- 📝 **Try**: Prompt templates:
  ```python
  from langchain.prompts import ChatPromptTemplate
  
  template = ChatPromptTemplate.from_messages([
      ("system", "You are a helpful coding assistant."),
      ("user", "Explain {concept} in simple terms")
  ])
  
  prompt = template.format_messages(concept="recursion")
  ```
- 🎯 **Task**: Build 3 prompt templates for your use cases

#### Day 13-14: Project - Chatbot v1
- 🎯 **Build**: Simple chatbot with memory
  ```python
  from langchain.memory import ConversationBufferMemory
  from langchain.chains import ConversationChain
  from langchain.llms import Ollama
  
  llm = Ollama(model="llama2")
  memory = ConversationBufferMemory()
  conversation = ConversationChain(llm=llm, memory=memory)
  
  response = conversation.predict(input="Hi! I'm learning LLMs")
  print(response)
  ```
- 🎯 **Task**: Create chatbot that remembers context across messages

**Week 2 Checkpoint**: ✅ You understand prompt engineering and built a chatbot

---

### **Week 3: RAG (Retrieval-Augmented Generation)** (Days 15-21)
*Goal: Build applications that use your own data*

#### Day 15-16: RAG Fundamentals
- 📖 Read: [RAG Paper](https://arxiv.org/abs/2005.11401) (intro/conclusion)
- 📺 Watch: [RAG Tutorial](https://www.youtube.com/watch?v=sVcwVQRHIc8) (30 min)
- 🎯 **Task**: Understand retrieval → augment → generate flow

#### Day 17-18: Vector Databases
- 🔧 **Install ChromaDB**:
  ```bash
  pip install chromadb
  ```
- 📝 **Try**: Store and retrieve documents:
  ```python
  import chromadb
  from chromadb.utils import embedding_functions
  
  client = chromadb.Client()
  collection = client.create_collection(
      name="my_docs",
      embedding_function=embedding_functions.DefaultEmbeddingFunction()
  )
  
  # Add documents
  collection.add(
      documents=["LLMs are powerful AI models"],
      ids=["doc1"]
  )
  
  # Query
  results = collection.query(
      query_texts=["What are LLMs?"],
      n_results=1
  )
  ```
- 🎯 **Task**: Index 20 documents, test retrieval

#### Day 19-21: Project - RAG Application
- 🎯 **Build**: Document Q&A system
  ```bash
  pip install langchain chromadb sentence-transformers
  ```
  
  ```python
  from langchain.document_loaders import DirectoryLoader
  from langchain.text_splitter import RecursiveCharacterTextSplitter
  from langchain.vectorstores import Chroma
  from langchain.embeddings import HuggingFaceEmbeddings
  from langchain.chains import RetrievalQA
  from langchain.llms import Ollama
  
  # Load documents
  loader = DirectoryLoader('./docs', glob="**/*.txt")
  documents = loader.load()
  
  # Split
  text_splitter = RecursiveCharacterTextSplitter(
      chunk_size=500,
      chunk_overlap=50
  )
  texts = text_splitter.split_documents(documents)
  
  # Create vector store
  embeddings = HuggingFaceEmbeddings()
  vectorstore = Chroma.from_documents(texts, embeddings)
  
  # Create QA chain
  llm = Ollama(model="llama2")
  qa = RetrievalQA.from_chain_type(
      llm=llm,
      retriever=vectorstore.as_retriever()
  )
  
  # Ask questions
  response = qa.run("What are the key points?")
  ```
- 🎯 **Task**: Build RAG system for your documents (PDFs, text files, etc.)

**Week 3 Checkpoint**: ✅ You built a RAG application with your own data

---

### **Week 4: Fine-Tuning & Production** (Days 22-30)
*Goal: Customize models and deploy applications*

#### Day 22-24: Fine-Tuning Basics
- 📖 Read: [LoRA Paper](https://arxiv.org/abs/2106.09685) (intro)
- 🔧 **Install**:
  ```bash
  pip install transformers peft datasets accelerate
  ```
- 📝 **Try**: Fine-tune small model (Google Colab with free GPU):
  ```python
  from transformers import AutoModelForCausalLM, AutoTokenizer, TrainingArguments
  from peft import LoraConfig, get_peft_model
  from datasets import load_dataset
  
  # Load model
  model = AutoModelForCausalLM.from_pretrained("gpt2")
  tokenizer = AutoTokenizer.from_pretrained("gpt2")
  
  # Configure LoRA
  lora_config = LoraConfig(
      r=8,
      lora_alpha=32,
      target_modules=["c_attn"],
      lora_dropout=0.1
  )
  
  model = get_peft_model(model, lora_config)
  # ... training code
  ```
- 🎯 **Task**: Fine-tune GPT-2 on custom dataset (use Colab GPU)

#### Day 25-27: Deployment
- 🔧 **Create FastAPI server**:
  ```bash
  pip install fastapi uvicorn
  ```
  
  ```python
  from fastapi import FastAPI
  from pydantic import BaseModel
  from langchain.llms import Ollama
  
  app = FastAPI()
  llm = Ollama(model="llama2")
  
  class Query(BaseModel):
      text: str
  
  @app.post("/chat")
  async def chat(query: Query):
      response = llm(query.text)
      return {"response": response}
  
  # Run: uvicorn main:app --reload
  ```
- 🎯 **Task**: Deploy your RAG app as an API

#### Day 28-30: Final Project
- 🎯 **Build**: Complete LLM application combining everything:
  1. **Frontend**: Simple web interface (Streamlit or Gradio)
  2. **Backend**: FastAPI with RAG
  3. **LLM**: Ollama for inference
  4. **Monitoring**: Basic logging

```bash
pip install streamlit
```

```python
import streamlit as st
from langchain.llms import Ollama
from langchain.vectorstores import Chroma
from langchain.embeddings import HuggingFaceEmbeddings
from langchain.chains import RetrievalQA

st.title("My LLM App 🤖")

# Initialize
@st.cache_resource
def setup():
    embeddings = HuggingFaceEmbeddings()
    vectorstore = Chroma(persist_directory="./db", embedding_function=embeddings)
    llm = Ollama(model="llama2")
    return RetrievalQA.from_chain_type(llm=llm, retriever=vectorstore.as_retriever())

qa = setup()

# Chat interface
user_input = st.text_input("Ask a question:")
if user_input:
    with st.spinner("Thinking..."):
        response = qa.run(user_input)
        st.write(response)

# Run: streamlit run app.py
```

**Week 4 Checkpoint**: ✅ You deployed a complete LLM application

---

## 🛠️ Essential Tools Setup

### Development Environment
```bash
# Create virtual environment
python -m venv llm-env
source llm-env/bin/activate  # On Windows: llm-env\Scripts\activate

# Core libraries
pip install transformers torch accelerate
pip install langchain langchain-openai
pip install chromadb sentence-transformers
pip install streamlit gradio fastapi uvicorn

# Optional but recommended
pip install jupyter ipython
pip install black flake8  # Code formatting
pip install python-dotenv  # Environment variables
```

### API Keys (Optional)
Create `.env` file:
```bash
OPENAI_API_KEY=your_key_here
ANTHROPIC_API_KEY=your_key_here
HUGGINGFACE_API_KEY=your_key_here
```

### GPU Setup (Optional)
```bash
# Check CUDA availability
python -c "import torch; print(torch.cuda.is_available())"

# Install CUDA version of PyTorch if needed
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

---

## 📚 Key Resources by Week

### Week 1 Resources
- [LLM Intro Video](https://www.youtube.com/watch?v=zjkBMFhNj_g) (Karpathy)
- [Ollama Documentation](https://ollama.ai/docs)
- [OpenAI API Docs](https://platform.openai.com/docs)

### Week 2 Resources
- [Prompt Engineering Guide](https://www.promptingguide.ai/)
- [LangChain Docs](https://python.langchain.com/docs/)
- [DeepLearning.AI Courses](https://www.deeplearning.ai/short-courses/)

### Week 3 Resources
- [LlamaIndex Documentation](https://docs.llamaindex.ai/)
- [ChromaDB Guide](https://docs.trychroma.com/)
- [RAG Paper](https://arxiv.org/abs/2005.11401)

### Week 4 Resources
- [Hugging Face Tutorials](https://huggingface.co/docs)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Streamlit Docs](https://docs.streamlit.io/)

---

## 🎯 Daily Routine

**For optimal learning:**
1. **Theory (30 min)**: Read documentation/watch video
2. **Practice (60 min)**: Write code, experiment
3. **Build (30 min)**: Work on weekly project
4. **Review (10 min)**: Document what you learned

**Total:** ~2 hours/day

---

## ✅ Progress Checklist

### Week 1: Foundations
- [ ] Watched Karpathy's LLM intro
- [ ] Used ChatGPT/Claude API
- [ ] Installed and ran Ollama locally
- [ ] Compared cloud vs local models

### Week 2: Prompting
- [ ] Tried zero-shot, few-shot, CoT prompts
- [ ] Installed LangChain
- [ ] Created prompt templates
- [ ] Built chatbot with memory

### Week 3: RAG
- [ ] Understood RAG architecture
- [ ] Set up ChromaDB
- [ ] Indexed documents
- [ ] Built Q&A system

### Week 4: Production
- [ ] Fine-tuned a model (optional)
- [ ] Created FastAPI endpoint
- [ ] Built Streamlit app
- [ ] Deployed complete application

---

## 🚧 Common Issues & Solutions

### Issue: "CUDA out of memory"
**Solution:** Use smaller batch size or smaller model, or use Colab

### Issue: "Module not found"
**Solution:** Ensure virtual environment activated: `source llm-env/bin/activate`

### Issue: "Ollama not found"
**Solution:** Restart terminal after installation, or use full path

### Issue: "API rate limit"
**Solution:** Use Ollama locally or get API key with higher limits

### Issue: "Slow inference"
**Solution:** Use quantized models (GGUF format), or GPU acceleration

---

## 🎓 What's Next?

### After 30 Days, Choose Your Path:

**Path A: Application Developer**
- Learn advanced RAG (hybrid search, reranking)
- Master agent frameworks (LangGraph, CrewAI)
- Production deployment (Docker, K8s)
- → Go to [07-Applications](./07-Applications/)

**Path B: Model Engineer**
- Deep dive into fine-tuning (LoRA, QLoRA, RLHF)
- Learn model optimization (quantization, pruning)
- Training infrastructure (DeepSpeed, Megatron)
- → Go to [03-Core-LLMs](./03-Core-LLMs/)

**Path C: MLOps Engineer**
- Production deployment patterns
- Monitoring and observability
- Cost optimization
- → Go to [06-Deployment-Ops](./06-Deployment-Ops/)

---

## 💡 Pro Tips

1. **Start small**: Don't try to fine-tune 70B models on day 1
2. **Use free resources**: Colab, Ollama, Hugging Face
3. **Join communities**: Discord servers, Reddit r/LocalLLaMA
4. **Document everything**: Keep notes on what works
5. **Build projects**: Learning by doing is crucial
6. **Ask for help**: Communities are very welcoming
7. **Stay updated**: Follow key people on Twitter/X

---

## 🔗 Quick Links

- **Main Repository**: [LLM-Engineering](./README.md)
- **FAQ**: [FAQ.md](./FAQ.md)
- **Glossary**: [GLOSSARY.md](./GLOSSARY.md)
- **Community**: [13-Community](./13-Community/)

---

**Ready to start? Begin with Day 1! 🚀**

**Last Updated:** October 2025
