# 📄 Multi-Utility RAG AI Agent using LangGraph & Streamlit

A **production-style Retrieval Augmented Generation (RAG) chatbot** built using **LangGraph, LangChain, Cerebras (Qwen), FAISS, and Streamlit**.

This chatbot can:

* 💬 Chat normally with memory
* 📄 Answer questions from uploaded PDFs (RAG)
* 🔧 Use tools like Web Search, Calculator, and Stock Price Fetching
* 🧵 Maintain multiple chat threads
* 💾 Persist conversations using SQLite

---

## 🚀 Features

### 🧠 Agentic AI (LangGraph)

* Graph-based agent workflow
* Tool calling with conditional routing
* Stateful conversations with persistence

### 📚 PDF-based RAG

* Upload PDFs per chat thread
* Chunking + embeddings using HuggingFace
* FAISS vector search for fast retrieval
* Thread-wise document indexing

### 🔧 Built-in Tools

* 🔍 Web Search (DuckDuckGo)
* 🧮 Calculator (add, sub, mul, div)
* 📈 Stock price lookup (Alpha Vantage API)
* 📄 RAG tool for PDF-based Q&A

### 💬 Chat Experience

* Streaming responses (token-by-token)
* Multi-threaded conversations
* Resume old chats
* Thread-specific memory & documents

### 💾 Persistence

* SQLite-based checkpointing
* Conversations survive app restarts
* Thread history is stored automatically

---

## 🏗️ Tech Stack

| Layer           | Technology                |
| --------------- | ------------------------- |
| LLM             | Cerebras Qwen-3-32B       |
| Agent Framework | LangGraph                 |
| LLM Interface   | LangChain                 |
| Embeddings      | HuggingFace (MiniLM)      |
| Vector DB       | FAISS                     |
| UI              | Streamlit                 |
| Persistence     | SQLite                    |
| Tools           | DuckDuckGo, Alpha Vantage |

---

## 📂 Project Structure

```text
rag-ai-agent/
│
├── rag_agent_backend.py     # LangGraph agent, tools, RAG logic
├── rag_agent_frontend                   # Streamlit frontend
├── chatbot.db               # SQLite database (auto-created)
├── .env                     # API keys & environment variables
├── requirements.txt         # Python dependencies
└── README.md                # Project documentation
```

---

## 🔄 High-Level Workflow

```text
User Message
   ↓
LangGraph Chat Node
   ↓
(If needed)
Tool Selection
   ├── Web Search
   ├── Calculator
   ├── Stock Price
   └── RAG Tool (PDF)
   ↓
Tool Result
   ↓
LLM Response
   ↓
Persist State (SQLite)
```

---

## 📄 How PDF RAG Works

1. User uploads a PDF
2. PDF is:

   * Loaded using PyPDFLoader
   * Split into chunks
   * Embedded using HuggingFace embeddings
3. Chunks are stored in FAISS
4. Each chat thread has its own retriever

When a question is asked:

* Relevant chunks are retrieved
* Context is injected into the LLM
* Answer is generated

---

## 🧠 Thread-Based Memory

* Each chat has a unique **thread ID**
* Threads store:

  * Conversation history
  * Indexed PDFs

Users can:

* Start a new chat
* Resume old chats
* Use different PDFs in different threads

---

## 🛠️ Tools Available

### 🧮 Calculator Tool

* Operations: add, sub, mul, div

### 🔍 Web Search Tool

* Powered by DuckDuckGo

### 📈 Stock Price Tool

* Uses Alpha Vantage API

### 📄 RAG Tool

* Retrieves relevant content from uploaded PDFs

---

## ▶️ How to Run the Project

### 1️⃣ Create virtual environment

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Set environment variables

Create a `.env` file:

```env
CEREBRAS_API_KEY=your_api_key_here
```

### 4️⃣ Run the Streamlit app

```bash
streamlit run app.py
```

---

## 📌 Example Use Cases

* Chat with your college notes PDFs
* Ask questions from research papers
* Financial queries using stock price tool
* Mixed conversations using tools + RAG
* Long-term chatbot memory

---

## 🧩 Future Enhancements

* 🔐 Authentication
* 📊 LangSmith observability
* 🧠 Hybrid RAG (BM25 + Vector)
* 🗂️ Multi-document comparison
* 🧪 Evaluation & feedback loop
* 🌐 Deployment (Docker / Cloud)

---

## 🙌 Acknowledgements

* LangChain & LangGraph team
* Cerebras Systems
* HuggingFace
* Streamlit community

---

⭐ **If you like this project**

Give it a ⭐ on GitHub and feel free to fork & extend it!
