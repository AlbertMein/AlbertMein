# Tool — Code Execution

## Purpose
Run code for data processing, calculations, or file transformations.

## When to Use
- Processing raw data into structured formats
- Calculating metrics or scores
- Transforming files between formats

## Inputs
- `language` — Python, bash, etc.
- `code` — Code to execute
- `timeout` — Max execution time in seconds (default: 30)

## Outputs
- stdout/stderr from execution
- Any files written to disk

## Constraints
- Never execute code that modifies files outside the workspace
- Never install packages without explicit approval
- Log execution time and exit code to `_logs/runs/`
