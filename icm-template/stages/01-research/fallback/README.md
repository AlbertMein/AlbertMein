# Fallback — 01-research

If this stage fails after max retries:

1. Log the failure reason to `_logs/errors/`
2. Save whatever partial research was gathered to `output/partial-notes.md`
3. Flag the output as incomplete: add `status: incomplete` to `_state/variables.yaml`
4. Proceed to next stage with a warning — downstream stages should check for incomplete flag
