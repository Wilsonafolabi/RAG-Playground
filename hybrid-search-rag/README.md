# Hybrid Search RAG

**Enterprise retrieval system combining sparse (BM25) and dense (vector) retrieval techniques.**

## 🎯 Goal

Develop a high-performance RAG system that leverages the strengths of both keyword-based and semantic search.

## ✨ Features

### Sparse Retrieval
- **BM25** - Classic probabilistic retrieval
- **Keyword Ranking** - Exact term matching
- **Boolean Filtering** - AND/OR/NOT queries

### Dense Retrieval
- **Semantic Embeddings** - Meaning-based search
- **Vector Similarity** - Cosine, dot-product, L2
- **Cross-Encoder Reranking** - Fine-grained relevance scoring

### Hybrid Pipeline
- **Fusion Scoring** - Reciprocal Rank Fusion (RRF)
- **Query Expansion** - Synonyms and related terms
- **Reranking** - Two-stage retrieval pipeline
- **Metadata-Aware Retrieval** - Filter before/after search

## 🏗️ Architecture

```
hybrid-search-rag/
├── backend/           # FastAPI server
├── ingestion/         # Document processing
├── indexing/          # Dual indexing (BM25 + vectors)
├── retrieval/         # Hybrid search engine
├── reranking/         # Cross-encoder reranking
├── generation/        # Answer synthesis
├── evaluation/        # Retrieval quality metrics
├── datasets/          # Test collections
└── notebooks/         # Fusion experiments
```

## 🛠️ Tech Stack

| Component | Technologies |
|-----------|-------------|
| **Search Engines** | Elasticsearch, OpenSearch |
| **Embeddings** | SentenceTransformers, BGE models |
| **Rerankers** | CrossEncoder, Cohere Rerank API |
| **Frameworks** | LangChain, LlamaIndex |

## 🚀 Quick Start

```bash
cd hybrid-search-rag
pip install -r requirements.txt

# Build dual index
python indexing/build_hybrid_index.py --docs ./datasets/

# Run hybrid search
python retrieval/search.py --query "machine learning applications" --top_k 10
```

## 📊 Performance Benefits

- **Better Recall:** Combines lexical and semantic matching
- **Higher Precision:** Reranking improves top results
- **Robust Queries:** Handles both exact terms and conceptual queries

## 📄 License

MIT License
