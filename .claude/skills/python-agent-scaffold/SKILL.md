---
name: python-agent-scaffold
description: "Scaffolds a new Python AI agent project with proper structure,
             config, and boilerplate. Use when creating a new agent, chain,
             or AI automation project from scratch."
---

## Scaffold Protocol

When creating a new Python AI agent project:

### Directory Structure
```
project-name/
├── src/
│   ├── __init__.py
│   ├── agent.py          # Main agent logic
│   ├── tools.py          # Agent tools/functions
│   ├── prompts.py        # System prompts and templates
│   └── config.py         # Pydantic settings
├── tests/
│   └── test_agent.py
├── .env.example           # Placeholder env vars
├── .gitignore
├── pyproject.toml
└── README.md
```

### .env.example must include
```
OPENAI_API_KEY=your-key-here
ANTHROPIC_API_KEY=your-key-here
# Add other keys as needed
```

### pyproject.toml must include
- Project metadata
- Dependencies with pinned versions
- Ruff configuration
- Pytest configuration

### Always include
- Type hints on all functions
- Docstrings on public functions
- Error handling for API calls with retries
- A basic pytest test file
