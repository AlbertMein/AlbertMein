## CrewAI Patterns
- Agents need: role, goal, backstory — make backstory specific to improve output
- Use `verbose=True` during development, disable in production
- Prefer `process=Process.sequential` unless tasks genuinely need delegation
- For hierarchical process, always define a manager_llm
- Custom tools must inherit from BaseTool and implement _run()
- Use `allow_delegation=False` on agents unless they specifically need to delegate
- Cache tool results with `cache_function` to reduce API costs
- Set `memory=True` on the crew for multi-step tasks that build on prior context
