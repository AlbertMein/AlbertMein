## LangChain Patterns
- Use LCEL (pipe syntax) for all new chains: `prompt | llm | parser`
- Prefer RunnablePassthrough and RunnableParallel for complex flows
- Use structured output with Pydantic models via `with_structured_output()`
- Callbacks for logging/tracing — never print inside chain logic
- Use LangSmith for debugging chains when available
- For RAG: always use RecursiveCharacterTextSplitter unless domain requires otherwise
- Chunk size 1000, overlap 200 as starting defaults — tune per use case
- Use MultiQueryRetriever or ContextualCompressionRetriever for better recall
