---
name: rag-setup
description: Set up RAG pipeline with LangChain, vector databases, embeddings
license: MIT
compatibility: opencode
metadata:
  audience: ml-engineers
  workflow: knowledge-base
---

## What I do

- Set up RAG with LangChain or LlamaIndex
- Configure vector stores (ChromaDB, Pinecone, Qdrant)
- Create embedding pipelines
- Build retrieval chains

## When to use me

Use this when building a knowledge base or document Q&A system.

## Quick Setup

```python
# LangChain RAG
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import HuggingFaceEmbeddings
from langchain.text_splitter import RecursiveCharacterTextSplitter

# Load documents
from langchain_community.document_loaders import PyPDFLoader
loader = PyPDFLoader("document.pdf")
documents = loader.load()

# Split
splitter = RecursiveCharacterTextSplitter(chunk_size=1000)
chunks = splitter.split_documents(documents)

# Embeddings
embeddings = HuggingFaceEmbeddings(model_name="BAAI/bge-small-en")

# Vector store
vectorstore = Chroma.from_documents(chunks, embeddings)

# Retriever
retriever = vectorstore.as_retriever()
```
