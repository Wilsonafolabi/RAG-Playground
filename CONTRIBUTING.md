# Contributing to RAG-Playground

Thank you for your interest in contributing! This guide will help you get started.

## 🚀 Getting Started

1. **Fork** the repository
2. **Clone** your fork: `git clone https://github.com/yourusername/RAG-Playground.git`
3. **Create a branch**: `git checkout -b feature/amazing-feature`
4. **Set up environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

## 📝 How to Contribute

### Code Contributions
- Follow existing code style (PEP 8)
- Add type hints to functions
- Write docstrings for public APIs
- Include unit tests for new features

### Documentation
- Update README files when adding features
- Add examples for new functionality
- Fix typos and clarify unclear sections

### Bug Reports
- Use GitHub Issues
- Include reproduction steps
- Share error messages and logs

### Feature Requests
- Open a GitHub Issue with the "enhancement" label
- Describe the use case clearly
- Explain why this feature would be valuable

## 🧪 Testing

```bash
# Run all tests
pytest

# Run specific project tests
pytest enterprise-document-rag/tests/

# Check code coverage
pytest --cov=shared/
```

## 📐 Code Style

```bash
# Format code
black .

# Lint code
flake8 .

# Type checking
mypy .
```

## 🔍 Pull Request Process

1. Ensure tests pass
2. Update documentation
3. Add entry to CHANGELOG.md (if applicable)
4. Request review from maintainers
5. Address feedback before merging

## 🤝 Community Guidelines

- Be respectful and inclusive
- Help others learn
- Give credit where due
- Focus on constructive feedback

## 📧 Contact

For questions, open an issue or contact maintainers directly.

Thank you for contributing! 🎉
