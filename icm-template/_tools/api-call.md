# Tool — API Call

## Purpose
Make HTTP requests to external APIs (LLM providers, data services, etc.).

## When to Use
- Calling LLM APIs for generation tasks
- Fetching data from external services
- Posting results to integrations

## Inputs
- `url` — API endpoint
- `method` — GET, POST, PUT, DELETE
- `headers` — Request headers (auth tokens from env vars)
- `body` — Request payload

## Outputs
- Response status code
- Response body

## Constraints
- Never hardcode API keys — always read from environment variables
- Implement retry with exponential backoff (2s, 4s, 8s)
- Set explicit timeouts (default: 30s)
- Log request/response metadata (NOT bodies) to `_logs/runs/`
- Track token usage and estimated cost for LLM API calls
