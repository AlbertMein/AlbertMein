---
name: git-workflow
description: >
  Standardized git commit and PR workflow. Use when committing changes,
  creating branches, or opening pull requests. Triggers on 'commit', 'push',
  'branch', 'PR', 'pull request', 'merge'.
argument-hint: [action: commit|branch|pr]
disable-model-invocation: true
---

# Git Workflow

You are a git workflow specialist. Follow conventional commits and feature branch strategy.

## Instructions

### 1. Determine Action

Based on $ARGUMENTS or context, determine the action:
- **commit** — Stage and commit changes
- **branch** — Create a feature branch
- **pr** — Create a pull request

### 2. Commit Workflow

When committing:

1. Run `git status` and `git diff --staged` to understand changes
2. Run `git log --oneline -5` to match existing commit style
3. Stage only relevant files (never `git add .` blindly)
4. Never stage `.env`, credentials, or large binaries
5. Write commit message in **conventional format**:
   - `feat:` new feature
   - `fix:` bug fix
   - `refactor:` code restructuring
   - `docs:` documentation
   - `test:` tests
   - `chore:` maintenance
6. Keep subject line under 72 characters
7. Add body with "why" for non-trivial changes
8. **Never amend published commits**
9. **Never force push**

### 3. Branch Workflow

When creating branches:

1. Always branch from `main` (fetch latest first)
2. Name format: `<type>/<short-description>`
   - `feat/add-auth-flow`
   - `fix/rate-limit-bug`
   - `refactor/extract-utils`
3. Push with `-u` to set upstream tracking

### 4. PR Workflow

When creating pull requests:

1. Run `git log main..HEAD --oneline` to review all commits
2. Run `git diff main...HEAD --stat` for change summary
3. Push branch to remote
4. Create PR with `gh pr create`:
   - Title: concise, under 70 chars
   - Body: ## Summary (bullets), ## Test Plan (checklist)
5. Never create PRs targeting `main` without review
6. Link related issues with "Closes #N" when applicable

### 5. Safety Rules

- Never push directly to `main` or `master`
- Never use `--force` or `--no-verify`
- Never skip pre-commit hooks
- Always verify `git status` after operations
- Warn if uncommitted changes exist before branching
