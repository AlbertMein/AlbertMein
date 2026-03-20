# Project Context

## Project
<!-- One-line description of what this workspace produces -->

## Objective
<!-- What is the end goal? What does "done" look like? -->

## Audience
<!-- Who consumes the final output? -->

## Constraints
- Token budget per stage: <!-- e.g., 4000 -->
- Max stages: <!-- e.g., 5 -->
- Tools available: see `_tools/`

## Stage Overview
| Stage | Purpose | Output |
|-------|---------|--------|
| 01-research | Gather source material | sources.md, raw notes |
| 02-analyze | Extract insights, identify patterns | analysis.md |
| 03-parallel | Draft deliverables concurrently | copy draft, visual specs |
| 04-review | Quality check, brand alignment | approved or rejected |
| 05-production | Final assembly and polish | final deliverable |

## Rules
- Load only the CONTEXT.md for the current stage — never preload all stages
- Every piece of information lives in exactly one place
- One-way references only — stages point forward, never backward
- Human review is expected between stages unless ROUTER.yaml says otherwise
