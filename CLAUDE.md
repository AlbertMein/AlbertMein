# CLAUDE.md — AlbertMein (GitHub Profile Repo)

## What Is This Repo?
This is my GitHub profile repository (AlbertMein/AlbertMein).
The README.md here shows up as my public GitHub profile page.

## My Tech Stack
- **Language:** Python
- **Domain:** AI automation — LLM agents, RAG pipelines, multi-agent systems
- **Frameworks:** LangChain, CrewAI, AutoGen, LlamaIndex
- **LLM APIs:** OpenAI, Anthropic, Google AI
- **Vector DBs:** Pinecone, FAISS, Weaviate
- **Infrastructure:** FastAPI, Docker, Pandas

---

## File & Folder Map (What Everything Is)

```
AlbertMein/                         <-- This repo (your GitHub profile)
│
├── README.md                       <-- Your public GitHub profile page
├── CLAUDE.md                       <-- THIS FILE — instructions Claude reads every session
├── .env.example                    <-- Template for API keys (safe to commit, no real keys)
├── .gitignore                      <-- Tells git which files to NEVER upload (secrets, junk)
├── .mcp.json                       <-- Connects Claude to external tools (docs lookup, reasoning)
│
├── .claude/                        <-- All Claude Code configuration lives here
│   ├── settings.json               <-- PERMISSIONS — what Claude is allowed/blocked from doing
│   ├── hooks.json                  <-- AUTOMATIONS — things that run before/after Claude acts
│   ├── rules/                      <-- RULES — instructions Claude must follow
│   │   ├── security.md             <--   "never commit API keys, never use eval()"
│   │   ├── python-conventions.md   <--   "use Python 3.10+, format with ruff"
│   │   └── ai-development.md       <--   "always retry API calls, log token usage"
│   ├── skills/                     <-- SKILLS — reusable workflows you trigger with /commands
│   │   ├── planning/               <--   /plan — break tasks into steps before coding
│   │   ├── tdd/                    <--   /tdd — write tests first, then code
│   │   ├── debugging/              <--   /debug — find the real cause of a bug
│   │   ├── code-review/            <--   /review — check code for bugs and security
│   │   ├── git-workflow/           <--   /commit — standardized git commits
│   │   ├── refactor/               <--   /refactor — clean up code safely
│   │   ├── security-audit/         <--   /security-audit — scan for vulnerabilities
│   │   ├── explain/                <--   /explain — explain how code works
│   │   ├── docs-gen/               <--   /docs-gen — auto-generate documentation
│   │   ├── python-agent-scaffold/  <--   /python-agent-scaffold — start a new AI project
│   │   ├── mcp-builder/            <--   /mcp-builder — build an MCP server
│   │   └── skill-creator/          <--   /skill-creator — create new skills
│   └── agents/                     <-- AGENTS — specialized helpers Claude can delegate to
│       └── research-agent.md       <--   researches AI tools, compares frameworks
│
└── repo-configs/                   <-- TEMPLATES — Claude configs for your other 7 repos
    ├── langchain-ai-automation/    <--   config template for that repo
    ├── crewai-multi-agent-systems/ <--   config template for that repo
    ├── autogen-agent-framework/    <--   ...
    ├── rag-document-processing/
    ├── ai-api-integration/
    ├── data-extraction-automation/
    └── ai-automation-templates/
```

---

## Naming Conventions — Why Things Are Named This Way

| Name | Why it's called that |
|------|---------------------|
| `.claude/` | Dot-folders (starting with `.`) are hidden by default — this keeps config out of your way |
| `settings.json` | Industry standard name for app configuration (JSON = structured data format) |
| `hooks.json` | "Hooks" = automatic triggers that fire before/after actions happen |
| `rules/*.md` | Markdown files (`.md`) with instructions Claude must follow, organized by topic |
| `skills/` | Each subfolder = one skill you can trigger with `/skill-name` |
| `SKILL.md` | The instruction file inside each skill folder — tells Claude what to do |
| `agents/` | Specialized AI assistants Claude can hand off sub-tasks to |
| `.mcp.json` | MCP = Model Context Protocol — connects Claude to external tools |
| `.env.example` | Template for environment variables — `.example` means "fill in your own values" |
| `.gitignore` | Tells git to ignore files matching these patterns (so secrets don't get uploaded) |
| `CLAUDE.md` | Named after Claude — this is the first file Claude reads in every session |
| `repo-configs/` | Ready-to-copy configuration templates for your other GitHub repositories |

---

## Rules for Claude

### Content Rules
- Keep README.md professional but approachable
- Do not add files unless they serve the profile repo purpose
- Links to repos must point to real AlbertMein repositories
- Do not add credentials, tokens, or API keys anywhere

### Workflow Rules
1. **Plan first** — Use `/plan` before non-trivial changes
2. **Test-driven** — Write failing tests before implementation (`/tdd`)
3. **Debug systematically** — Use `/debug`, not guess-and-check
4. **Review before commit** — Use `/review` to check quality and security
5. **Format with ruff** — Python files are auto-formatted via hook

---

## Quick Reference — Slash Commands You Can Use

| Command | What it does |
|---------|-------------|
| `/plan` | Breaks a task into ordered steps before you start |
| `/tdd` | Write tests first, then make them pass |
| `/debug` | Systematically find the root cause of a bug |
| `/review` | Check code for bugs, security issues, and style |
| `/commit` | Create a clean, conventional git commit |
| `/refactor` | Restructure code without breaking it |
| `/security-audit` | Scan code for security vulnerabilities |
| `/explain` | Explain how a piece of code works |
| `/docs-gen` | Auto-generate documentation from code |
| `/python-agent-scaffold` | Scaffold a new Python AI agent project |
| `/mcp-builder` | Guide for building an MCP server |
| `/skill-creator` | Create a new custom skill |

**Built-in (always available):**

| Command | What it does |
|---------|-------------|
| `/simplify` | Review changed code for quality and efficiency |
| `/claude-api` | Load Claude API docs (auto-triggers on `anthropic` import) |

---

## MCP Servers (External Tools)
- **Context7** (v2.1.3) — Fetches real, current library documentation at query time
- **Sequential Thinking** (v2025.12.18) — Structured step-by-step reasoning for complex problems

## Security Layers
1. **settings.json** — Blocks destructive commands (`rm -rf`, `sudo`, force-push) and credential access
2. **hooks.json** — Blocks pushes to main, blocks `curl|bash`, auto-formats Python with ruff
3. **rules/security.md** — "Never commit API keys, never use eval()"
4. **.gitignore** — Prevents `.env` files, IDE configs, and Python junk from being uploaded
