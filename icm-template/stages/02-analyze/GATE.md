# Gate — 02-analyze

## Entry Conditions
- [ ] `../01-research/output/sources.md` exists
- [ ] `../01-research/output/raw-notes.md` exists

## Exit Criteria
- [ ] `output/analysis.md` exists with structured insights
- [ ] `output/key-points.md` exists
- [ ] All claims reference stage 01 sources

## On Failure
- Retry up to `max_retries` (see ROUTER.yaml)
- If retries exhausted → execute `fallback/` instructions
- Log failure to `_logs/errors/`
