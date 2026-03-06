# CLAUDE.md — ai-automation-templates

## Overview
Starter templates and boilerplate for AI automation projects. Copy, customize, build.

## Tech Stack
- Language: Python 3.10+
- Frameworks: LangChain, CrewAI, AutoGen, LlamaIndex
- Common deps: Pydantic, python-dotenv, httpx, ruff
- Testing: pytest
- Linting: ruff

## Folder Structure
- /templates            One directory per template
  - /langchain-agent    Basic LangChain agent starter
  - /crewai-crew        Basic CrewAI crew starter
  - /rag-pipeline       Basic RAG pipeline starter
  - /fastapi-llm        FastAPI + LLM API starter
  - /data-extractor     Scraping + LLM extraction starter
- /shared               Shared utilities across templates
- /tests                Template validation tests

## Build Commands
- `pytest`              Validate templates
- `ruff check .`        Lint all templates

## Conventions
- Each template is self-contained — copy the folder and it works
- Every template includes: pyproject.toml, .env.example, .gitignore, README.md
- Templates use placeholder values (YOUR_API_KEY, your-project-name)
- Keep templates minimal — just enough to get started, not a full app
- All templates must include basic error handling and logging
- Test that each template's imports resolve and basic structure is valid
- NEVER include real API keys in templates — always placeholders
- Update templates when framework major versions change
