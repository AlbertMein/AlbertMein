# Stage 03 — Parallel Drafting

## Mode
**Parallel** — Sub-stages `03a` and `03b` run concurrently.

## Fork Behavior
- Both sub-stages receive the same inputs from stage 02
- Each operates independently with its own CONTEXT.md contract
- Neither sub-stage should reference the other's output

## Join Behavior
- **Wait for all** — both must complete before proceeding to stage 04
- Outputs from both sub-stages are available to stage 04

## Sub-Stages
| Sub-Stage | Purpose | Output |
|-----------|---------|--------|
| 03a-draft-copy | Write the text/copy deliverable | draft copy |
| 03b-draft-visuals | Specify visual elements | visual specs, layouts |

## On Partial Failure
- If one sub-stage fails, the other continues
- Stage 04 reviews whatever completed successfully
- Failed sub-stage is logged and flagged for manual intervention
