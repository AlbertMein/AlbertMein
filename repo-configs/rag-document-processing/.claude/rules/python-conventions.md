## Python Conventions
- Use Python 3.10+ features (match/case, type unions with |)
- Structure projects with src/ layout when appropriate
- Use Pydantic for config and data validation
- Async by default for I/O-bound operations (aiohttp, httpx)
- Use structured logging (structlog or loguru) over print statements
- Requirements: use pyproject.toml or requirements.txt with pinned versions
- Format with ruff, lint with ruff — single tool for both
