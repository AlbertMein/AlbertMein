# CLAUDE.md — AlbertMein (GitHub Profile Repo)

## Overview
This is my GitHub profile repository (AlbertMein/AlbertMein).
It contains my README.md which serves as my public GitHub profile page.

## Tech Focus
- Primary language: Python
- Domain: AI automation — LLM agents, RAG pipelines, multi-agent systems
- Frameworks: LangChain, CrewAI, AutoGen, LlamaIndex
- LLM APIs: OpenAI, Anthropic, Google AI
- Vector DBs: Pinecone, FAISS, Weaviate
- Infrastructure: FastAPI, Docker, Pandas

## Repo Structure
- /README.md — GitHub profile page (public-facing)
- /.claude/ — Claude Code configuration (skills, hooks, rules)
- /.mcp.json — MCP server configurations

## Conventions
- Keep README.md professional but approachable (matches my voice)
- Do not add files unless they serve the profile repo purpose
- Any links to repos must point to real AlbertMein repositories
- Do not add credentials, tokens, or API keys anywhere

## Workflow — How Claude Should Work Here
1. **Plan first** — Use `/plan` or the planning skill before non-trivial changes
2. **Test-driven** — Write failing tests before implementation (TDD skill)
3. **Debug systematically** — Use `/debug` and the debugging skill, not guess-and-check
4. **Review before commit** — Use `/review` to check changes for quality and security
5. **Format with ruff** — Python files are auto-formatted via PostToolUse hook

## Available Skills

### Core Workflow
- `planning` — Structured task decomposition (Understand → Plan → Validate → Execute)
- `tdd` — Red-green-refactor test-driven development
- `debugging` — Systematic root cause analysis
- `code-review` — Security, quality, and correctness checklist
- `git-workflow` — Standardized commits, branches, and PRs

### Code Quality
- `refactor` — Systematic refactoring with safety guarantees
- `security-audit` — Deep OWASP/CVE vulnerability scanning
- `explain` — Code explanation and onboarding walkthroughs
- `docs-gen` — Auto-generate documentation from code

### Building
- `python-agent-scaffold` — Scaffold new Python AI agent projects
- `mcp-builder` — Guide for creating MCP servers (Python/TypeScript)
- `skill-creator` — Create, test, and iterate on new skills (from Anthropic)

### Built-in (ships with Claude Code)
- `claude-api` — Build apps with Claude API / Anthropic SDK / Agent SDK
- `simplify` — Review changed code for reuse, quality, and efficiency

## MCP Servers
- **Context7** — Fetches real, current library documentation at query time
- **Sequential Thinking** — Structured step-by-step reasoning for complex problems

## Security
- Dangerous commands are blocked via PreToolUse hooks
- Deny rules in settings.json prevent destructive operations
- Python files are auto-linted with ruff on save via PostToolUse hooks
- Never commit .env files — use .env.example with placeholders
