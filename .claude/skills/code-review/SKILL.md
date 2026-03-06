---
name: code-review
description: "Code review checklist. Use when reviewing PRs, auditing code, or
             performing quality checks before merging."
---

## Code Review Protocol

When reviewing code, check each category systematically:

### 1. Correctness
- Does the code do what it claims to do?
- Are edge cases handled (empty inputs, None, boundary values)?
- Are error paths tested?

### 2. Security (OWASP-aware)
- [ ] No hardcoded secrets, API keys, or credentials
- [ ] User input is validated and sanitized
- [ ] SQL queries use parameterized statements
- [ ] No eval()/exec() with untrusted input
- [ ] Dependencies are pinned to specific versions
- [ ] No sensitive data in logs

### 3. Python Quality
- [ ] Type hints on all function signatures
- [ ] Follows existing code style (ruff-compliant)
- [ ] Imports ordered: stdlib → third-party → local
- [ ] No unnecessary complexity (cyclomatic complexity < 10)
- [ ] f-strings used consistently (not .format() or %)

### 4. Testing
- [ ] New logic has corresponding tests
- [ ] Tests cover happy path AND error cases
- [ ] External APIs are mocked
- [ ] No flaky tests (time-dependent, order-dependent)

### 5. Performance
- [ ] No N+1 queries or unnecessary loops
- [ ] Large data processed in batches/streams
- [ ] Async used for I/O-bound operations

### Output Format
```
## Review: [file or PR]

### ✅ Looks Good
- [thing that's well done]

### ⚠️ Suggestions
- [file:line] — [suggestion and why]

### 🚫 Must Fix
- [file:line] — [issue and why it must change]
```
