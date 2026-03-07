# How Claude Code Configuration Works

This guide explains every file in the `.claude/` folder in plain language.

---

## The Big Picture

Think of Claude Code like hiring an assistant. This folder contains:

1. **What they're allowed to do** → `settings.json`
2. **Automatic safety checks** → `hooks.json`
3. **Standing instructions** → `rules/` folder
4. **Reusable workflows** → `skills/` folder
5. **Specialist helpers** → `agents/` folder

---

## File-by-File Breakdown

### settings.json — "The Permission Slip"

Controls what Claude can and cannot do. Three lists:

- **allow** = "Go ahead, no need to ask me" (e.g., running tests, reading files)
- **deny** = "NEVER do this, even if I accidentally ask" (e.g., delete everything, access my SSH keys)
- **ask** = "Check with me first" (default for anything not in allow/deny)

**Example:** `"Bash(rm -rf *)"` in the deny list means Claude can never run a "delete everything" command, even if you tell it to.

### hooks.json — "The Safety Net"

Automatic checks that run before or after Claude does something:

- **PreToolUse** = Runs BEFORE Claude acts. Can block dangerous actions.
  - Blocks `rm -rf` (mass deletion)
  - Blocks pushing code to main branch
  - Blocks downloading and running unknown scripts

- **PostToolUse** = Runs AFTER Claude acts. Used for cleanup.
  - Auto-formats Python files with ruff after every edit

### rules/ — "The Rulebook"

Markdown files with instructions Claude follows. Organized by topic:

| File | What it tells Claude |
|------|---------------------|
| `security.md` | Never commit secrets, validate user input, pin dependency versions |
| `python-conventions.md` | Use Python 3.10+, Pydantic, async, ruff formatting |
| `ai-development.md` | Retry API calls, log token costs, use streaming, cache responses |

### skills/ — "The Playbooks"

Each folder is a reusable workflow you trigger with a `/command`. Inside each folder, `SKILL.md` contains the step-by-step instructions.

**Think of skills like recipes:** instead of explaining what you want every time, you just say `/plan` and Claude follows the planning playbook.

### agents/ — "The Specialists"

Definition files for specialized sub-assistants Claude can delegate tasks to. For example, `research-agent.md` defines a research specialist that compares AI frameworks and provides recommendations.

---

## How It All Connects

```
You type a message
       ↓
Claude reads CLAUDE.md (project instructions)
       ↓
Claude reads rules/ (security, Python, AI rules)
       ↓
Claude decides what tool to use
       ↓
hooks.json PreToolUse checks run → BLOCKS if dangerous
       ↓
settings.json checks → BLOCKS if denied, ASKS if not allowed
       ↓
Claude executes the action
       ↓
hooks.json PostToolUse runs → auto-formats Python files
       ↓
Claude responds to you
```

---

## Where Things Are Saved (All Locations)

| Location | Scope | Shared via git? |
|----------|-------|-----------------|
| `~/.claude/CLAUDE.md` | Your personal preferences (all projects) | No |
| `~/.claude/settings.json` | Your global permissions | No |
| `./CLAUDE.md` | This project's instructions | Yes |
| `./.claude/settings.json` | This project's permissions | Yes |
| `./.claude/hooks.json` | This project's automations | Yes |
| `./.claude/rules/` | This project's rules | Yes |
| `./.claude/skills/` | This project's skills | Yes |
| `./.claude/settings.local.json` | Your personal overrides (this project only) | No (.gitignored) |
