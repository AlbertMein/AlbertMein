## Scraping & Extraction Patterns
- Always add User-Agent headers — never use default Python UA
- Implement politeness delays: minimum 1s between requests to same domain
- Use session/connection pooling for multi-page scrapes
- Handle common failures: 403, 429, CAPTCHA, redirects
- For LLM extraction: provide 2-3 examples in the prompt for consistent output
- Validate extracted data against Pydantic schema immediately — fail fast
- Log extraction confidence/quality metrics when possible
- Use CSS selectors over XPath for readability
- Playwright: always use headless mode in production, headed for debugging
