# CLAUDE.md — langchain-ai-automation

## Overview
LangChain agents, chains, and RAG pipelines for AI automation tasks.

## Tech Stack
- Language: Python 3.10+
- Framework: LangChain / LangGraph
- LLM Providers: OpenAI, Anthropic, Google AI
- Vector DBs: FAISS, Pinecone, Weaviate
- Embeddings: OpenAI text-embedding-3-small, HuggingFace
- Testing: pytest
- Linting: ruff

## Folder Structure
- /agents           LangChain agent implementations
- /chains           Custom chain definitions
- /rag              RAG pipeline components (loaders, splitters, retrievers)
- /tools            Custom tools for agents
- /prompts          Prompt templates and system messages
- /tests            Test files mirroring src structure
- /examples         Usage examples and notebooks

## Build Commands
- `pip install -e .`        Install in dev mode
- `pytest`                  Run tests
- `ruff check .`            Lint
- `ruff format .`           Format

## Conventions
- Each agent gets its own file in /agents/
- Prompt templates live in /prompts/ — never hardcode prompts inline
- All LLM calls must go through LangChain abstractions — no raw API calls
- Use LCEL (LangChain Expression Language) for new chains
- Store API keys in .env — use python-dotenv to load them
- NEVER commit .env files
