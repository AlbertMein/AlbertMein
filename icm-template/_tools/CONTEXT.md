# Tools — Agent Capabilities

## Routing Rules
- Only use tools specified in the current stage's CONTEXT.md
- Each tool is defined as a markdown contract below
- Log every tool invocation to `_logs/runs/`
- Respect rate limits and cost budgets

## Available Tools
| Tool | File | When to Use |
|------|------|-------------|
| Web Search | `web-search.md` | Research stages — finding sources and references |
| Code Execution | `code-exec.md` | Data processing, calculations, file transformations |
| API Call | `api-call.md` | External service integration (LLM APIs, data APIs) |

## Adding New Tools
1. Create a new `.md` file in this directory
2. Follow the contract template: Name, Purpose, Inputs, Outputs, Constraints
3. Reference it in the relevant stage's CONTEXT.md
