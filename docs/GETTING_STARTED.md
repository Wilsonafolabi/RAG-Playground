# Getting Started with RAG-Playground

This guide will help you set up and start using the RAG-Playground repository.

## Prerequisites

- Python 3.9 or higher
- pip package manager
- Git
- (Optional) GPU for faster model inference

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/RAG-Playground.git
cd RAG-Playground
```

### 2. Create Virtual Environment

```bash
python -m venv venv

# On Linux/Mac
source venv/bin/activate

# On Windows
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
# Install core dependencies
pip install -r requirements.txt

# Or install minimal dependencies for a specific project
pip install -r enterprise-document-rag/requirements.txt
```

### 4. Set Up Environment Variables

Create a `.env` file in the root directory:

```bash
# LLM API Keys (if using cloud models)
OPENAI_API_KEY=your_key_here
ANTHROPIC_API_KEY=your_key_here

# Vector Database Configuration
QDRANT_URL=http://localhost:6333
CHROMA_PATH=./chroma_db

# Other Configuration
LOG_LEVEL=INFO
```

## Quick Start Tutorial

### Step 1: Choose Your Project

Start with **Enterprise Document RAG** for document understanding:

```bash
cd enterprise-document-rag
```

### Step 2: Prepare Your Documents

Place your PDF files in the `datasets/` folder:

```bash
mkdir -p datasets/documents
cp /path/to/your/document.pdf datasets/documents/
```

### Step 3: Ingest Documents

```bash
python ingestion/ingest.py --path datasets/documents/
```

### Step 4: Query Your Documents

```bash
python retrieval/query.py --question "What are the main findings?"
```

## Project Structure Overview

```
RAG-Playground/
├── enterprise-document-rag/    # Start here for PDF chatbots
├── structured-data-rag/        # For SQL/database queries
├── hybrid-search-rag/          # For advanced search
├── graph-rag-system/           # For knowledge graphs
├── multimodal-medical-rag/     # For medical imaging
├── vision-retrieval-rag/       # For image/video search
└── agentic-rag/                # For multi-agent systems
```

## Common Tasks

### Add New Documents

```bash
python ingestion/ingest.py --path /path/to/new/docs --project enterprise-document-rag
```

### Run Evaluation

```bash
python evaluation/run_eval.py --dataset test_set.json
```

### Start API Server

```bash
python backend/server.py --host 0.0.0.0 --port 8000
```

## Troubleshooting

### Out of Memory Errors

- Reduce batch size in configuration
- Use CPU instead of GPU for small workloads
- Enable gradient checkpointing

### Model Download Issues

```bash
# Clear Hugging Face cache
rm -rf ~/.cache/huggingface

# Retry download
pip install --upgrade huggingface_hub
```

### Vector Database Connection Errors

```bash
# Check if database is running
docker ps | grep qdrant

# Restart database
docker restart qdrant
```

## Next Steps

1. Read individual project READMEs for detailed guides
2. Explore notebooks for example code
3. Join community discussions on GitHub
4. Contribute your own improvements!

## Resources

- [LangChain Documentation](https://python.langchain.com/)
- [Hugging Face Models](https://huggingface.co/models)
- [Vector Database Guides](https://qdrant.tech/documentation/)

Happy building! 🚀
