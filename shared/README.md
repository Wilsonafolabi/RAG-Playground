# Shared Infrastructure

This directory contains reusable modules and utilities shared across all RAG projects in this repository.

## 📁 Module Structure

```
shared/
├── embeddings/          # Embedding pipelines for text, images, multimodal
├── vectorstores/        # Vector database abstractions (FAISS, Qdrant, Chroma)
├── evaluation/          # Metrics: Recall@K, Faithfulness, Hallucination rate
├── chunking/            # Semantic, layout-aware, hierarchical chunking
├── rerankers/           # Cross-encoder reranking, reciprocal rank fusion
└── utils/               # Helper functions, config loaders, logging
```

## 🔧 Modules

### 1. Embeddings (`embeddings/`)
Unified interface for generating embeddings across modalities:

**Features:**
- Text embeddings (BGE, InstructorXL, Jina)
- Image embeddings (CLIP, BioCLIP)
- Multimodal embeddings
- Batch processing
- Caching mechanisms

**Usage:**
```python
from shared.embeddings import EmbeddingManager

# Initialize
embedder = EmbeddingManager(model_name="BAAI/bge-large-en")

# Text embedding
text_embedding = embedder.embed_text("Your query here")

# Image embedding
image_embedding = embedder.embed_image("path/to/image.jpg")

# Batch embedding
embeddings = embedder.embed_batch(texts=["text1", "text2", ...])
```

---

### 2. Vector Stores (`vectorstores/`)
Abstracted vector database operations:

**Supported Backends:**
- FAISS (CPU/GPU)
- Qdrant
- ChromaDB

**Features:**
- Unified API across different backends
- Metadata filtering
- Similarity search (cosine, dot product, L2)
- Index persistence and loading
- Hybrid search support

**Usage:**
```python
from shared.vectorstores import VectorStoreFactory

# Create vector store
store = VectorStoreFactory.create(backend="faiss", dimension=768)

# Add documents
store.add_documents(embeddings=embeddings, metadata=metadata_list)

# Search
results = store.search(query_embedding, k=10, filters={"source": "doc1"})
```

---

### 3. Evaluation (`evaluation/`)
Comprehensive RAG evaluation metrics:

**Metrics:**
- **Retrieval Metrics:** Recall@K, Precision@K, NDCG, MRR
- **Generation Metrics:** Faithfulness, Answer Relevance
- **Hallucination Detection:** Fact consistency checks
- **Context Metrics:** Context relevance, Context precision
- **Performance:** Latency, Throughput

**Usage:**
```python
from shared.evaluation import RAGEvaluator

evaluator = RAGEvaluator()

# Evaluate retrieval
retrieval_score = evaluator.evaluate_retrieval(
    retrieved_docs=retrieved,
    ground_truth=relevant_docs
)

# Evaluate generation
generation_score = evaluator.evaluate_generation(
    question=question,
    answer=generated_answer,
    contexts=retrieved_contexts
)

# Full pipeline evaluation
full_report = evaluator.evaluate_pipeline(dataset=test_dataset)
```

---

### 4. Chunking (`chunking/`)
Advanced document chunking strategies:

**Strategies:**
- **Fixed-size:** Simple character/token-based splitting
- **Semantic:** Meaning-preserving boundaries using NLP
- **Layout-aware:** Respect document structure (headers, tables)
- **Hierarchical:** Multi-level chunks (page → section → paragraph)
- **Recursive:** Intelligent recursive splitting with separators

**Usage:**
```python
from shared.chunking import ChunkingStrategy

# Semantic chunking
chunker = ChunkingStrategy(strategy="semantic", chunk_size=512)
chunks = chunker.chunk(document_text)

# Layout-aware chunking (for PDFs)
chunker = ChunkingStrategy(strategy="layout_aware")
chunks = chunker.chunk_from_pdf("document.pdf")

# Hierarchical chunking
chunker = ChunkingStrategy(strategy="hierarchical", levels=["page", "section", "paragraph"])
chunks = chunker.chunk(document_text)
```

---

### 5. Rerankers (`rerankers/`)
Post-retrieval reranking for improved relevance:

**Methods:**
- **Cross-Encoder:** BERT-based reranking (ms-marco, bge-reranker)
- **Reciprocal Rank Fusion (RRF):** Combine multiple retrieval results
- **LLM-based:** Use LLM to score relevance
- **Metadata boosting:** Boost results based on metadata

**Usage:**
```python
from shared.rerankers import RerankerFactory

# Cross-encoder reranker
reranker = RerankerFactory.create(method="cross_encoder", model="bge-reranker-large")
reranked_results = reranker.rerank(query=query, documents=retrieved_docs, top_k=5)

# Reciprocal Rank Fusion
reranker = RerankerFactory.create(method="rrf")
fused_results = reranker.fuse([results_bm25, results_dense], top_k=10)
```

---

### 6. Utilities (`utils/`)
Common helper functions and configurations:

**Includes:**
- Configuration management (YAML/JSON loaders)
- Logging setup
- Progress tracking
- File I/O helpers
- Data preprocessing utilities
- Model caching
- Environment variable management

**Usage:**
```python
from shared.utils import load_config, setup_logging, ProgressBar

# Load configuration
config = load_config("config.yaml")

# Setup logging
logger = setup_logging(level="INFO")

# Progress tracking
with ProgressBar(total=100) as pbar:
    for item in items:
        process(item)
        pbar.update(1)
```

---

## 🚀 Installation

```bash
# Install shared module dependencies
pip install -r requirements.txt

# Or install individual components
pip install sentence-transformers faiss-cpu qdrant-client
```

---

## 📝 Best Practices

1. **Reuse, Don't Duplicate:** Always check if a utility exists before creating new ones
2. **Type Hints:** Use Python type hints for better IDE support
3. **Documentation:** Document all public functions and classes
4. **Testing:** Write unit tests for shared utilities
5. **Version Control:** Keep shared modules backward compatible
6. **Configuration:** Use config files instead of hardcoding values

---

## 🧪 Testing

```bash
# Run tests for shared modules
pytest shared/tests/

# Run specific module tests
pytest shared/embeddings/test_embeddings.py
pytest shared/evaluation/test_metrics.py
```

---

## 🤝 Contributing

When adding new shared utilities:

1. Ensure the utility is genuinely reusable across multiple projects
2. Write comprehensive docstrings
3. Add unit tests
4. Update this README
5. Follow existing code style

---

## 📄 License

MIT License - See main repository LICENSE file