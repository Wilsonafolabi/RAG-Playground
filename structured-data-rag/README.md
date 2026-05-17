# Structured Data / SQL RAG

**Enable LLMs to interact intelligently with structured databases and business datasets.**

## 🎯 Goal

Build a RAG system that can understand database schemas, generate SQL queries from natural language, and provide business insights from structured data.

## ✨ Features

### Data Sources
- **SQL Databases** - PostgreSQL, SQLite, MySQL
- **CSV Files** - Tabular data ingestion
- **Excel Sheets** - Spreadsheet parsing
- **JSON APIs** - Structured API responses

### AI Capabilities
- **Natural Language to SQL** - Convert questions to queries
- **Data Analysis** - Automatic aggregations and statistics
- **Chart Generation** - Visualize query results
- **Business Insights** - Summarize findings in plain English

### Advanced Features
- **Schema Understanding** - Learn table relationships
- **Query Validation** - Check SQL correctness before execution
- **SQL Correction** - Fix malformed queries
- **Multi-Table Joins** - Handle complex queries

## 🏗️ Architecture

```
structured-data-rag/
├── backend/              # FastAPI server
├── ingestion/            # Data source connectors
├── schema_analyzer/      # Schema understanding
├── retrieval/            # Table/column search
├── sql_generator/        # NL-to-SQL conversion
├── generation/           # Insight generation
├── evaluation/           # SQL accuracy metrics
├── datasets/             # Sample databases
└── notebooks/            # SQL experiments
```

## 🛠️ Tech Stack

| Component | Technologies |
|-----------|-------------|
| **Database** | PostgreSQL, SQLite |
| **Data Tools** | Pandas, SQLAlchemy |
| **Frameworks** | LangChain SQL Agent, FastAPI |

## 🚀 Quick Start

```bash
cd structured-data-rag
pip install -r requirements.txt

# Connect to database
python ingestion/connect_db.py --db postgresql://localhost/mydb

# Query in natural language
python sql_generator/query.py --question "Show top 10 customers by revenue"
```

## 📝 Example Queries

```
Question: "What was the total sales in Q4 2023?"
Generated SQL: SELECT SUM(amount) FROM sales WHERE date BETWEEN '2023-10-01' AND '2023-12-31'

Question: "Which product category has the highest margin?"
Generated SQL: SELECT category, AVG(margin) as avg_margin FROM products GROUP BY category ORDER BY avg_margin DESC LIMIT 1
```

## 📄 License

MIT License
