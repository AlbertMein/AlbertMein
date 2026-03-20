# Gate — 05-production

## Entry Conditions
- [ ] `../04-review/output/review.md` exists with PASS decision
- [ ] All draft outputs from stage 03 are available

## Exit Criteria
- [ ] Final deliverable written to `output/`
- [ ] `output/manifest.md` documents what was produced
- [ ] Run logged to `_logs/runs/`

## On Failure
- Log to `_logs/errors/`
- Save partial output for manual completion
- Flag in `_state/variables.yaml` as `production_incomplete: true`
