# Neural Reranked RAG System with GPT-Neo

This repository implements a Retrieval-Augmented Generation (RAG) system featuring a two-stage retrieval pipeline. It uses a Bi-Encoder for initial dense retrieval and a Cross-Encoder for neural reranking to provide high-quality context to an EleutherAI GPT-Neo model.

## 🚀 Key Features

- **Generator:** Uses `EleutherAI/gpt-neo-1.3B` for generating context-aware answers.
- **Bi-Encoder Retrieval:** Utilizes `all-MiniLM-L6-v2` for fast, semantic search across document embeddings.
- **Cross-Encoder Reranking:** Implements `cross-encoder/ms-marco-MiniLM-L6-v2` to re-score and refine the top retrieved candidates for maximum relevancy.
- **Vector Search:** Powered by **FAISS** (Facebook AI Similarity Search) for efficient nearest-neighbor indexing.

## 🛠️ Architecture Overview

The system operates in four distinct stages:
1. **Embedding & Indexing:** Documents are vectorized and stored in a FAISS FlatL2 index.
2. **Retrieval:** A query is encoded and the top 10 candidates are fetched via vector similarity.
3. **Reranking:** These 10 candidates are re-evaluated against the query using a neural Cross-Encoder to select the top 3 most relevant segments.
4. **Generation:** The final context and query are passed to GPT-Neo to synthesize a natural language response.
