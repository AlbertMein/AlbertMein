## Security Rules
- NEVER commit API keys, tokens, or credentials
- NEVER create .env files with real values — use .env.example with placeholders
- Always validate and sanitize user input at API boundaries
- Use parameterized queries — never string-concatenated SQL
- Never use eval() or exec() with untrusted input
- Pin dependency versions to avoid supply chain attacks
