---
name: code-review
description: "Use when reviewing PRs, auditing code, checking quality before merge, or when
             the user says 'review', 'audit', 'check'. Security, correctness, and quality
             checklist with mandatory verification."
---

# Code Review

## Overview
Every review follows a structured checklist — nothing is skipped because it "looks fine."
**Core principle:** Review is verification, not skimming. Read every changed line.

**"Violating the letter of the rules is violating the spirit of the rules."**

## The Iron Law
```
NO APPROVAL WITHOUT CHECKING EVERY ITEM ON THE CHECKLIST
```

## When to Use
- **Always:** Before merging PRs, before committing multi-file changes
- **Sometimes:** After refactoring, after adding new dependencies
- **Never:** Typo-only changes, documentation-only changes

## The Checklist

### 1. Security (check FIRST — highest priority)
- [ ] No hardcoded secrets, API keys, tokens, or credentials
- [ ] No `.env` files with real values (only `.env.example` with placeholders)
- [ ] User input is validated and sanitized at API boundaries
- [ ] SQL queries use parameterized statements (no string concatenation)
- [ ] No `eval()` or `exec()` with untrusted input
- [ ] Dependencies are pinned to specific versions
- [ ] No sensitive data in logs or error messages
- [ ] No overly permissive CORS, permissions, or file access

### 2. Correctness
- [ ] Code does what it claims to do (read the implementation, don't assume)
- [ ] Edge cases handled: empty inputs, None/null, boundary values, large inputs
- [ ] Error paths are tested and don't silently swallow failures
- [ ] Async operations have proper error handling and timeouts
- [ ] Race conditions considered for concurrent code

### 3. Python Quality
- [ ] Type hints on all function signatures
- [ ] Follows existing code style (ruff-compliant)
- [ ] Imports ordered: stdlib → third-party → local
- [ ] No unnecessary complexity (functions under 100 lines, cyclomatic complexity < 10)
- [ ] f-strings used consistently
- [ ] `pathlib.Path` over `os.path`

### 4. Testing
- [ ] New logic has corresponding tests
- [ ] Tests cover happy path AND error cases
- [ ] External APIs are mocked — never hit real endpoints
- [ ] No flaky tests (time-dependent, order-dependent, network-dependent)

### 5. Performance
- [ ] No N+1 queries or unnecessary nested loops
- [ ] Large data processed in batches/streams
- [ ] Async used for I/O-bound operations
- [ ] No unnecessary recomputation (cache where appropriate)

## Red Flags — Must Fix Before Approval
If you find ANY of these, it's a mandatory fix:
- Hardcoded credentials or API keys
- SQL injection vulnerabilities
- Missing input validation on user-facing endpoints
- `eval()`/`exec()` with external input
- Tests that hit real external APIs
- Unpinned dependencies

## Output Format
```
## Review: [file or PR title]

### 🚫 Must Fix (blocking)
- [file:line] — [issue and why it must change]

### ⚠️ Suggestions (non-blocking)
- [file:line] — [suggestion and why]

### ✅ Looks Good
- [thing that's well done]
```

## Announcement
Always say: "I'm using the code-review skill to review [target]."
