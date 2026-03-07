# CLAUDE.md — crewai-multi-agent-systems

## Overview
Multi-agent systems built with CrewAI. Crews of specialized agents collaborating on complex tasks.

## Tech Stack
- Language: Python 3.10+
- Framework: CrewAI
- LLM Providers: OpenAI, Anthropic
- Tools: CrewAI Tools, LangChain Tools, custom tools
- Testing: pytest
- Linting: ruff

## Folder Structure
- /crews            Crew definitions (agents + tasks + process)
- /agents           Individual agent role definitions
- /tasks            Task definitions
- /tools            Custom tools for agents
- /config           YAML config files for crews
- /tests            Test files
- /examples         Usage examples

## Build Commands
- `pip install -e .`        Install in dev mode
- `pytest`                  Run tests
- `ruff check .`            Lint

## Conventions
- Each crew gets its own directory under /crews/
- Define agents in YAML config when possible — keeps them declarative
- One agent = one clear role/expertise (don't make swiss-army-knife agents)
- Tasks must have clear expected_output descriptions
- Use sequential process for simple flows, hierarchical for complex ones
- Always set max_iter on agents to prevent infinite loops
- Log crew execution results for cost tracking
- NEVER let agents make real API calls in tests — always mock
