# CLAUDE.md — autogen-agent-framework

## Overview
Multi-agent conversations and workflows using Microsoft AutoGen.

## Tech Stack
- Language: Python 3.10+
- Framework: AutoGen (pyautogen)
- LLM Providers: OpenAI, Anthropic, local models
- Testing: pytest
- Linting: ruff

## Folder Structure
- /conversations    Multi-agent conversation setups
- /agents           Custom agent definitions
- /skills           Code execution skills for agents
- /config           OAI_CONFIG_LIST and agent configs
- /tests            Test files
- /examples         Usage examples

## Build Commands
- `pip install -e .`        Install in dev mode
- `pytest`                  Run tests
- `ruff check .`            Lint

## Conventions
- Store LLM configs in OAI_CONFIG_LIST format — never hardcode API keys
- Use ConversableAgent as base class for custom agents
- Always set max_consecutive_auto_reply to prevent runaway conversations
- Code execution must happen in Docker containers — never allow local execution in production
- Use human_input_mode="TERMINATE" for automated flows, "ALWAYS" for interactive
- Group chats need a clear speaker_selection_method
- NEVER commit OAI_CONFIG_LIST with real keys
