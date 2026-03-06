# CLAUDE.md — data-extraction-automation

## Overview
Web scraping combined with LLM-powered data extraction and structuring.

## Tech Stack
- Language: Python 3.10+
- Scraping: BeautifulSoup, Playwright, Scrapy
- LLM Extraction: LangChain, OpenAI function calling
- Data Processing: Pandas, Pydantic
- Storage: JSON, CSV, SQLite, PostgreSQL
- Testing: pytest
- Linting: ruff

## Folder Structure
- /scrapers         Web scraping modules (one per source/site)
- /extractors       LLM-powered data extraction pipelines
- /schemas          Pydantic models defining expected data shapes
- /transformers     Data cleaning and transformation
- /storage          Output adapters (file, database, API)
- /tests            Test files with fixture HTML/data
- /examples         Usage examples

## Build Commands
- `pip install -e .`        Install in dev mode
- `pytest`                  Run tests
- `ruff check .`            Lint

## Conventions
- Always define output schema with Pydantic BEFORE building the extractor
- Use Playwright for JS-heavy sites, BeautifulSoup for static HTML
- Respect robots.txt — add rate limiting and delays between requests
- Cache raw HTML/responses during development to avoid re-scraping
- LLM extraction must use structured output (function calling or Pydantic)
- NEVER hardcode URLs or selectors — make them configurable
- Store scraped data samples in /tests/fixtures/ for reproducible tests
- NEVER commit scraped data to Git
