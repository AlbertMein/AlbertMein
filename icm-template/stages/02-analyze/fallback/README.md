# Fallback — 02-analyze

If this stage fails after max retries:

1. Log failure to `_logs/errors/`
2. Pass stage 01 raw notes directly to stage 03 as-is
3. Set `analysis_skipped: true` in `_state/variables.yaml`
4. Stage 03 sub-stages should compensate by doing lightweight analysis inline
