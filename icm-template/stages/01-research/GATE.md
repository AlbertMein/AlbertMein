# Gate — 01-research

## Entry Conditions
- [ ] Root CONTEXT.md has been read
- [ ] Project objective is clear

## Exit Criteria
- [ ] `output/sources.md` exists with at least 3 verified sources
- [ ] `output/raw-notes.md` exists and is organized by topic
- [ ] No unverified claims in the notes

## On Failure
- Retry up to `max_retries` (see ROUTER.yaml)
- If retries exhausted → execute `fallback/` instructions
- Log failure to `_logs/errors/`
