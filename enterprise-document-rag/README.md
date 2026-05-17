# Enterprise Document RAG

**Production-style document intelligence system for complex PDFs, scanned documents, tables, and page-level citations.**

## 🎯 Goal

Build a production-ready RAG system capable of understanding and retrieving information from enterprise documents with layout awareness, table extraction, and citation-grounded generation.

## ✨ Features

### Document Processing
- **PDF Ingestion** - Parse text, metadata, and structure
- **OCR Support** - Handle scanned documents with PaddleOCR
- **Table Extraction** - Extract and index tabular data
- **Layout-Aware Parsing** - Understand document structure (headers, sections, columns)
- **Multi-Page Indexing** - Track content across pages

### Retrieval
- **Page-Aware Retrieval** - Retrieve with page context
- **Chunk-Level Retrieval** - Fine-grained semantic search
- **Hierarchical Indexing** - Page → Section → Paragraph hierarchy
- **Semantic Search** - Vector similarity with BGE embeddings
- **Metadata Filtering** - Filter by source, date, author, etc.

### Generation
- **Citation-Grounded Answers** - Every claim backed by sources
- **Page References** - "See page 5, section 3.2"
- **Context Summarization** - Concise summaries of retrieved content
- **Multi-Document Reasoning** - Synthesize information across documents

## 🏗️ Architecture

```
enterprise-document-rag/
├── backend/           # FastAPI server, API endpoints
├── frontend/          # Web UI (React/Streamlit)
├── ingestion/         # PDF parsing, OCR, table extraction
├── indexing/          # Hierarchical indexing pipeline
├── retrieval/         # Page-aware and chunk-level retrieval
├── generation/        # LLM integration, citation grounding
├── evaluation/        # Quality metrics, benchmarks
├── datasets/          # Sample documents
└── notebooks/         # Exploration and prototyping
```

## 🛠️ Tech Stack

| Component | Technologies |
|-----------|-------------|
| **Parsing & OCR** | PyMuPDF, pdfplumber, PaddleOCR, Unstructured |
| **Embeddings** | BAAI/bge-large-en, InstructorXL |
| **Vector DB** | FAISS, Qdrant, ChromaDB |
| **Frameworks** | LangChain, LlamaIndex, FastAPI |
| **LLM** | GPT-4, Claude, Llama-3, Mistral |

## 🚀 Quick Start

```bash
# Navigate to project
cd enterprise-document-rag

# Install dependencies
pip install -r requirements.txt

# Run ingestion pipeline
python ingestion/ingest.py --path ./datasets/sample.pdf

# Start retrieval server
python backend/server.py

# Query the system
curl -X POST http://localhost:8000/query \
  -H "Content-Type: application/json" \
  -d '{"query": "What is the revenue in Q4?", "top_k": 5}'
```

## 📊 Advanced Features (Roadmap)

### Phase 2
- [ ] Hybrid retrieval (BM25 + Dense)
- [ ] Query expansion
- [ ] Reranking pipeline
- [ ] Document summarization

### Phase 3
- [ ] Multi-document comparison
- [ ] Long-context memory
- [ ] Streaming retrieval
- [ ] Agentic routing

## 📈 Evaluation Metrics

- **Retrieval:** Recall@K, Precision@K, NDCG
- **Generation:** Faithfulness, Answer Relevance
- **Citation Quality:** Citation accuracy, Page reference correctness
- **Performance:** Latency, Throughput

## 📝 Usage Examples

### Basic Query
```python
from retrieval.retriever import DocumentRetriever

retriever = DocumentRetriever(index_path="./indexes/my_docs")
results = retriever.search("What are the key findings?", top_k=5)

for result in results:
    print(f"Page {result.page}: {result.text}")
    print(f"Citation: {result.citation}")
```

### Table Query
```python
from retrieval.table_retriever import TableRetriever

table_retriever = TableRetriever()
results = table_retriever.search_table("Q4 revenue by region")
```

## 🤝 Contributing

See main repository contributing guidelines.

## 📄 License

MIT License