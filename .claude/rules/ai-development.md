## AI/LLM Development Rules
- Always implement retry logic with exponential backoff for LLM API calls
- Use streaming for user-facing LLM responses
- Log token usage and estimated costs where practical
- Store embeddings in vector DBs — never recompute on every query
- Use chunking strategies appropriate to the document type for RAG
- Implement proper rate limiting when calling external LLM APIs
- Cache LLM responses when the input is deterministic and results are reusable
- Always set temperature and max_tokens explicitly — never rely on defaults
