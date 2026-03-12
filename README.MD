# Intelligent Document Q&A Assistant (Agentic RAG)

## Overview
This project implements an intelligent document assistant that ingests large PDF documents, builds a knowledge base using Retrieval-Augmented Generation (RAG), and routes user queries to the appropriate tool.  
The system supports summarization, general question answering with citations, and an additional approach tool for structured guidance from the document.

---

## Architecture

PDF → DocEater → MyWIKI (FAISS) → Hero (Dispatcher) → Tool → LLM → Output

---

## Modules

### DocEater()
Handles document ingestion:
- Loads PDF using PyPDFLoader  
- Cleans and chunks text  
- Prepares data for embedding  

---

### MyWIKI()
- Converts chunks into embeddings  
- Stores embeddings in FAISS vector database  
- Enables retrieval for RAG pipeline  

---

### TellInShort()
- Generates structured summaries  
- Uses truncated document context (first portion of the document) to ensure efficient and stable summarization within token limits.

---

### AnswerMe()
- Retrieves relevant chunks  
- Generates grounded answers  
- Displays citations (page-based)

---

### ApproachHow()
- Provides structured guidance  
- Useful for methodology/assignment-based documents  

---

### Hero()
- Central dispatcher module  
- Routes queries to tools using keyword-based intent logic  

---

### UI()
- Built using Gradio  
- Supports PDF upload + querying interface  

---

## Features

- PDF ingestion pipeline  
- RAG-based retrieval  
- Multi-tool routing system  
- Page-based citations  
- Interactive UI  

---

## Sample Document

A sample test document is included in this repository:
- **ResearchPaper.pdf** (Attention Is All You Need)
This document can be used to quickly test the system without needing to upload your own PDF.

Suggested test queries:
- summarize this document  
- what is the main idea  
- approach for testing methodology

## How to Run

### 1. Install Dependencies

```
pip install -r requirements.txt
````

---

### 2. Add OpenRouter API Key

Add your OpenRouter API key using one of the following:

**Option 1 (Recommended – Colab Secrets):**

* Open Colab → Secrets
* Add key with name: `StepUp`
* Run notebook normally

**Option 2 (Environment Variable):**

```
export OPENAI_API_KEY="your_key"
```

---

### 3. Run Notebook

* Execute all cells
* Launch UI

---

### 4. Use the System

* Upload PDF (10+ pages)
* Ask queries like:

```
summarize this document  
what is the main idea  
approach for testing methodology
```

---

## Future Scope

* LLM-based intent classification and tool call
* UI improvements
* Deployment as web app
