# Retrieval-Augmented Generation (RAG) on PDF Document

## Project Overview

This project implements a **Retrieval-Augmented Generation (RAG)** system using a Harvard Business Review (HBR) article titled:

**"How Apple Is Organized for Innovation"**

The system retrieves relevant information from the PDF document and generates context-aware answers using a language model. The goal is to demonstrate how Large Language Models (LLMs) can be enhanced with external knowledge sources to improve factual accuracy and reduce hallucinations.

---

## What is RAG?

Retrieval-Augmented Generation (RAG) is a framework that combines:

1. **Retrieval** – Searching relevant information from a knowledge source.
2. **Generation** – Using a language model to generate an answer based on retrieved context.

Instead of relying only on pre-trained knowledge, RAG grounds responses in actual documents.

---

## RAG Architecture

The pipeline follows these steps:

PDF Document → Text Extraction  → Text Chunking → Embedding Generation → FAISS Vector Store → User Query → Embedding → Similarity Search (Top-K Retrieval) → LLM Generation (Context + Question) → Final Answer

---

## Dataset / Knowledge Source

- **Type:** PDF Document  
- **Source:** Harvard Business Review Article  
- **File Used:** `HBR_How_Apple_Is_Organized_For_Innovation-4.pdf`  
- **Nature:** Public article  

---

## Text Chunking Strategy

- **Chunk Size:** 500 characters  
- **Chunk Overlap:** 100 characters  

### Reason:
- Prevents context loss at chunk boundaries  
- Maintains semantic continuity  
- Improves retrieval accuracy  

---

## Embedding Model

- **Model Used:** `sentence-transformers/all-MiniLM-L6-v2`

### Reason for Selection:
- Lightweight and fast  
- Good semantic similarity performance  
- Works efficiently on CPU (Google Colab)  

---

## Vector Database

- **Vector Store Used:** FAISS (Facebook AI Similarity Search)

### Why FAISS?
- Fast similarity search  
- Efficient dense vector indexing  
- No external API required  
- Suitable for local experimentation  

---

## Language Model Used

- **Model:** `google/flan-t5-base`

Used to generate answers based on retrieved document context.

---

## Tools and Libraries Used

- Python  
- Sentence Transformers  
- FAISS  
- HuggingFace Transformers  
- PyPDF  
- NumPy  
- Google Colab  

---

## Implementation Steps

1. Install required libraries  
2. Upload the PDF file  
3. Extract text from PDF  
4. Split text into chunks  
5. Generate embeddings for chunks  
6. Store embeddings in FAISS  
7. Convert user query into embedding  
8. Retrieve top-k relevant chunks  
9. Pass retrieved context to LLM  
10. Generate final answer  

---

## Sample Test Queries

Example queries tested:

1. How is Apple organized for innovation?  
2. What is the role of functional structure at Apple?  
3. What leadership characteristics does Apple emphasize?  

The system retrieves relevant context from the document and generates grounded responses.

---

## Future Improvements

- Semantic chunking instead of fixed-size chunking  
- Hybrid search (keyword + vector search)  
- Reranking using cross-encoders  
- Metadata filtering (page-based filtering)  
- Streamlit / Gradio UI integration  
- Deployment as a web application  

---

## How to Run (Google Colab)

1. Open the notebook in Google Colab  
2. Install dependencies:

   ```bash
   !pip install sentence-transformers faiss-cpu transformers pypdf

