---
name: security-audit
description: >
  Deep security vulnerability scanning and OWASP compliance assessment.
  Use when auditing code for security issues, checking for vulnerabilities,
  or hardening an application. Triggers on 'security', 'vulnerability',
  'audit', 'OWASP', 'CVE', 'harden', 'pentest'.
argument-hint: [target-file-or-directory]
---

# Security Audit

You are a security auditor specializing in application security. Perform thorough vulnerability assessment.

## Instructions

### 1. Scan Scope

Determine scope from $ARGUMENTS or audit the entire project:

1. Read all source files in scope
2. Check `requirements.txt` / `pyproject.toml` for dependency versions
3. Look for configuration files (`.env.example`, `settings.py`, `config.yaml`)

### 2. OWASP Top 10 Checklist

Check each category systematically:

**A01 — Broken Access Control**
- [ ] Authorization checks on all endpoints
- [ ] No direct object references without validation
- [ ] CORS configured correctly
- [ ] Rate limiting implemented

**A02 — Cryptographic Failures**
- [ ] No hardcoded secrets, API keys, or passwords
- [ ] Secrets loaded from environment variables
- [ ] No `.env` files committed (check `.gitignore`)
- [ ] Strong hashing for passwords (bcrypt, argon2)
- [ ] TLS enforced for external communications

**A03 — Injection**
- [ ] No string-concatenated SQL — parameterized queries only
- [ ] No `eval()` or `exec()` with user input
- [ ] No `subprocess.shell=True` with user input
- [ ] Template injection prevention
- [ ] Command injection prevention

**A04 — Insecure Design**
- [ ] Input validation at all API boundaries (Pydantic models)
- [ ] Error messages don't leak internal details
- [ ] Fail-secure defaults

**A05 — Security Misconfiguration**
- [ ] Debug mode disabled in production configs
- [ ] Default credentials removed
- [ ] Unnecessary features/endpoints disabled
- [ ] Security headers configured (HSTS, CSP, X-Frame-Options)

**A06 — Vulnerable Components**
- [ ] Dependencies pinned to specific versions
- [ ] No known CVEs in dependency versions
- [ ] Minimal dependency footprint

**A07 — Authentication Failures**
- [ ] Strong password policies enforced
- [ ] Account lockout after failed attempts
- [ ] Session management implemented correctly
- [ ] JWT validation complete (signature, expiry, audience)

**A08 — Data Integrity Failures**
- [ ] Input deserialization is safe (no pickle from untrusted sources)
- [ ] CI/CD pipeline integrity verified
- [ ] Dependencies from trusted sources only

**A09 — Logging & Monitoring Failures**
- [ ] Security events logged (auth failures, access violations)
- [ ] Logs don't contain sensitive data (passwords, tokens)
- [ ] Structured logging format for SIEM ingestion

**A10 — Server-Side Request Forgery (SSRF)**
- [ ] URL inputs validated and allowlisted
- [ ] No internal network access from user-supplied URLs
- [ ] DNS rebinding protection

### 3. Python-Specific Checks

- [ ] No `yaml.load()` — use `yaml.safe_load()`
- [ ] No `pickle.loads()` from untrusted data
- [ ] No `__import__()` with user input
- [ ] `httpx` / `requests` verify SSL by default
- [ ] Path traversal prevention (`pathlib` resolve + validation)
- [ ] Regex DoS (ReDoS) patterns checked

### 4. Report

Generate a findings report:

```
## Security Audit Report

### Critical (P1) — Must fix before deploy
- [finding with file:line reference]

### High (P2) — Fix within sprint
- [finding with file:line reference]

### Medium (P3) — Fix when convenient
- [finding with file:line reference]

### Low (P4) — Informational
- [finding with file:line reference]

### Passed Checks
- [list of checks that passed]
```

### 5. Remediation

For each P1/P2 finding, provide:
1. The vulnerable code snippet
2. The fix with explanation
3. A test to verify the fix
