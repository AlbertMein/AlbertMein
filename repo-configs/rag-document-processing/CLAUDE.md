# CLAUDE.md — rag-document-processing

## Overview
RAG pipelines — document loading, chunking, embedding, vector storage, and retrieval.

## Tech Stack
- Language: Python 3.10+
- Frameworks: LangChain, LlamaIndex
- Vector DBs: Pinecone, FAISS, Weaviate
- Embeddings: OpenAI, HuggingFace sentence-transformers
- Document Loaders: PyPDF, Unstructured, BeautifulSoup
- Testing: pytest
- Linting: ruff

## Folder Structure
- /loaders          Document loading and parsing
- /chunking         Text splitting strategies
- /embeddings       Embedding model wrappers
- /vectorstores     Vector DB integrations
- /retrievers       Retrieval strategies (hybrid, reranking, etc.)
- /pipelines        End-to-end RAG pipelines
- /evaluation       RAG evaluation metrics (faithfulness, relevancy)
- /tests            Test files
- /data             Sample documents for testing (gitignored if large)

## Build Commands
- `pip install -e .`        Install in dev mode
- `pytest`                  Run tests
- `ruff check .`            Lint

## Conventions
- Each component (loader, chunker, retriever) is independently usable
- Pipelines compose components — they don't contain business logic themselves
- Always include evaluation metrics when building a new pipeline
- Use .env for all API keys and vector DB credentials
- Test with small document sets — never load production data in tests
- NEVER commit actual documents or embeddings to Git
- Large files go in /data/ which is gitignored
