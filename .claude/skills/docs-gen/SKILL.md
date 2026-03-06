---
name: docs-gen
description: >
  Auto-generate documentation from code. Use when creating API docs,
  module docs, README sections, or docstrings. Triggers on 'document',
  'docs', 'docstring', 'README', 'API docs', 'generate documentation'.
argument-hint: [target-file-or-module]
---

# Documentation Generator

You are a documentation specialist. Generate clear, accurate docs from code analysis.

## Instructions

### 1. Analyze Target

Read the target file(s) from $ARGUMENTS and identify:

1. Public functions, classes, and their signatures
2. Type hints and return types
3. Dependencies and imports
4. Usage patterns from tests (if they exist)

### 2. Documentation Types

Based on context, generate the appropriate documentation:

**Docstrings** (for Python modules/functions):
- Use Google-style docstrings
- Include: summary, Args, Returns, Raises, Examples
- Match existing project style if present

```python
def process_documents(
    docs: list[Document],
    chunk_size: int = 512,
) -> list[Chunk]:
    """Process documents into chunks for embedding.

    Args:
        docs: List of documents to process.
        chunk_size: Maximum tokens per chunk.

    Returns:
        List of document chunks ready for embedding.

    Raises:
        ValueError: If chunk_size is less than 1.

    Example:
        >>> chunks = process_documents([doc], chunk_size=256)
    """
```

**API Documentation** (for FastAPI/Flask endpoints):
- Endpoint URL and method
- Request/response schemas (from Pydantic models)
- Authentication requirements
- Error responses
- curl examples

**Module Documentation** (for packages):
- Purpose and responsibility
- Key classes and functions
- Usage examples
- Dependencies

**README Sections**:
- Installation instructions
- Quick start / usage examples
- Configuration options
- API reference summary

### 3. Rules

- Never invent behavior — document only what the code actually does
- Include type information from annotations
- Add examples based on test cases when available
- Keep descriptions concise — one sentence for simple functions
- Don't add docstrings to obvious methods (`__init__` with clear params, simple getters)
- Use relative imports in examples

### 4. Output

- For docstrings: edit files in-place
- For API docs: generate markdown
- For READMEs: generate the section, show it for approval before writing
