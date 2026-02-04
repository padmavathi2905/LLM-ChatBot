# 🤖 RAG-Based LLM Chatbot

A **Retrieval Augmented Generation  based AI chatbot** built using a **fully open source stack**.  
This application allows users to upload PDF documents, generate embeddings, and interact with their documents through an intelligent chatbot all running **locally** for privacy and control.

<img width="1502" height="599" alt="Screenshot 2026-02-04 at 11 29 14 AM" src="https://github.com/user-attachments/assets/b94e639e-8773-4c89-a36c-60eeeecaab56" />

<img width="1502" height="650" alt="Screenshot 2026-02-04 at 11 29 20 AM" src="https://github.com/user-attachments/assets/93c3145e-f062-422d-b618-25941bb5ac40" />

---

## 📌 Project Overview

The **RAG-Based LLM Chatbot** is a **Streamlit-powered web application** that enables document-based question answering.  
By combining **semantic search** with a **local Large Language Model (LLM)**, the chatbot provides accurate, context-aware answers grounded in uploaded documents.

---

## ✨ Features

- 📂 **Upload PDF Documents**  
  Upload and preview PDF files directly in the app.

- 🧠 **Create Embeddings**  
  Generate semantic embeddings for documents using **BGE embeddings**.

- 🗄️ **Vector Storage with Qdrant**  
  Store and retrieve document embeddings efficiently using a local Qdrant vector database.

- 🤖 **Intelligent Chatbot**  
  Ask natural language questions and get accurate answers from your documents.

- 🔐 **Local & Private**  
  No external APIs required — runs completely on your machine.

- 🖥️ **User-Friendly UI**  
  Clean and intuitive Streamlit interface.

---

## 🧠 RAG Architecture (How It Works)

1. **PDF Upload** → User uploads a document  
2. **Text Extraction + OCR** → Text extracted using `unstructured`  
3. **Embeddings Creation** → BGE embeddings generated  
4. **Vector Storage** → Stored in Qdrant  
5. **Query Embedding** → User question embedded  
6. **Semantic Retrieval** → Relevant chunks retrieved  
7. **Answer Generation** → LLaMA 3.2 generates a grounded response  

---

## 🛠️ Tech Stack

### Core Technologies
- **Python 3.10**
- **Streamlit** – UI framework
- **LangChain** – RAG orchestration
- **Qdrant** – Vector database (Docker-based)
- **Ollama** – Local LLM runtime

### Models & Libraries
- **LLaMA 3.2 (via Ollama)** – Local LLM
- **BGE Embeddings (BAAI/bge-small-en)** – Semantic embeddings
- **sentence-transformers**
- **unstructured + OCR (Tesseract)** – PDF text extraction

---


---

## 🚀 Getting Started

### Clone the Repository

---

```bash

# ================================
# RAG-Based LLM Chatbot Setup
# ================================

# 1. Clone the repository
git clone https://github.com/padmavathi2905/LLM-Chatbot.git
cd LLM-Chatbot

# 2. Create and activate virtual environment (Python 3.10 recommended)
python3.10 -m venv venv --upgrade-deps
source venv/bin/activate

# 3. Upgrade pip tools
python -m pip install --upgrade pip setuptools wheel

# 4. Install Python dependencies
python -m pip install -r requirements.txt

# 5. Install Unstructured with full PDF + OCR support
python -m pip install "unstructured[pdf,image,ocr]"

# 6. Fix NumPy compatibility (LangChain requires numpy < 2)
python -m pip install "numpy<2"

# 7. Install OpenCV (NumPy-compatible, headless)
python -m pip install "opencv-python-headless<4.9"

# 8. Install PDF image conversion dependency
python -m pip install pdf2image

# 9. Install system dependencies (macOS)
brew install poppler tesseract

# 10. Set OCR engine
export OCR_AGENT=tesseract

# 11. Pull LLaMA model using Ollama
ollama pull llama3.2:3b

# 12. Start Qdrant using Docker
docker run -d \
  --name qdrant \
  -p 6333:6333 \
  qdrant/qdrant

# 13. Run the Streamlit application
python -m streamlit run new.py
