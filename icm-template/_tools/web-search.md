# Tool — Web Search

## Purpose
Search the web for current information, sources, and references.

## When to Use
- Stage 01 (research) — primary tool
- Any stage that needs to verify a fact

## Inputs
- `query` — Search query string
- `max_results` — Number of results to return (default: 5)

## Outputs
- List of results with title, URL, snippet

## Constraints
- Verify source credibility before citing
- Prefer recent sources (< 1 year old) unless historical context needed
- Log queries and result counts to `_logs/runs/`
