## API Integration Patterns
- Use exponential backoff with jitter for retries (tenacity library)
- Set hard timeouts on all API calls (30s default, configurable)
- Implement circuit breaker pattern for provider failover
- Normalize streaming to async generators across all providers
- Token counting: use tiktoken for OpenAI, anthropic.count_tokens for Claude
- Cost tracking: map model names to per-token pricing, log per-request
- Use Pydantic for all request/response validation
- Provider-specific features (function calling, vision, etc.) go in provider modules, not the base interface
- Always handle rate limit errors (429) specifically — back off longer
