# CLAUDE.md — ai-api-integration

## Overview
Unified wrappers for LLM APIs — OpenAI, Anthropic Claude, Google Gemini, and others.

## Tech Stack
- Language: Python 3.10+
- APIs: OpenAI, Anthropic, Google AI (Gemini), Cohere, Mistral
- HTTP: httpx (async), requests (sync fallback)
- Validation: Pydantic
- Testing: pytest, pytest-asyncio
- Linting: ruff

## Folder Structure
- /providers        One module per LLM provider (openai.py, anthropic.py, etc.)
- /models           Pydantic models for requests/responses
- /middleware        Retry logic, rate limiting, caching, cost tracking
- /utils            Shared utilities (token counting, streaming helpers)
- /tests            Test files with mocked API responses
- /examples         Usage examples

## Build Commands
- `pip install -e .`        Install in dev mode
- `pytest`                  Run tests
- `ruff check .`            Lint

## Conventions
- Every provider implements the same base interface (abstract class)
- All API calls go through the retry middleware — never call APIs directly
- Response models are provider-agnostic — normalize all responses to a common shape
- Track token usage and cost on every call
- Use async by default — provide sync wrappers where needed
- NEVER store API keys in code — always load from environment
- Tests must use mocked responses — never hit real APIs in CI
