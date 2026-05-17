# GraphRAG Knowledge System

**Graph-enhanced retrieval system using knowledge graphs and entity relationships.**

## 🎯 Goal

Build a RAG system that leverages knowledge graphs for multi-hop reasoning and entity-centric retrieval.

## ✨ Features

### Knowledge Extraction
- **Entity Extraction** - Identify people, organizations, concepts
- **Relation Extraction** - Discover relationships between entities
- **Graph Construction** - Build Neo4j knowledge graphs

### Graph Retrieval
- **Graph Traversal** - Navigate entity relationships
- **Semantic Neighborhood** - Retrieve related concepts
- **Context-Aware Querying** - Enrich queries with graph context

### Reasoning
- **Relationship Discovery** - Find implicit connections
- **Multi-Hop Reasoning** - Answer complex queries requiring multiple hops
- **Context Enrichment** - Expand retrieval with graph neighbors

## 🏗️ Architecture

```
graph-rag-system/
├── backend/              # API server
├── ingestion/            # Entity/relation extraction
├── knowledge_graph/      # Neo4j graph construction
├── retrieval/            # Graph traversal & semantic search
├── generation/           # Graph-augmented generation
├── evaluation/           # Graph retrieval metrics
├── datasets/             # Sample knowledge graphs
└── notebooks/            # Graph analysis
```

## 🛠️ Tech Stack

| Component | Technologies |
|-----------|-------------|
| **Graph Database** | Neo4j, NetworkX, PyVis |
| **NLP** | spaCy, Hugging Face Transformers |
| **Retrieval** | GraphRAG, LangChain |

## 🚀 Quick Start

```bash
cd graph-rag-system
pip install -r requirements.txt

# Build knowledge graph
python knowledge_graph/build.py --input ./datasets/texts/

# Query with graph augmentation
python retrieval/query.py --question "What companies did Elon Musk found?"
```

## 📄 License

MIT License
