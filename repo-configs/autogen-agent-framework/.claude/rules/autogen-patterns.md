## AutoGen Patterns
- Always define termination conditions: is_termination_msg or max_turns
- Use register_function() for tool use — cleaner than inline code
- GroupChat needs explicit max_round to prevent infinite loops
- For code generation agents: always review generated code before execution
- Use teachable agents for tasks that benefit from learning across sessions
- Cache LLM responses with Cache.disk() during development to save costs
- Use nested chats for complex sub-task delegation
- System messages should be specific about output format expectations
