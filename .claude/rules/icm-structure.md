## Extended ICM Structure — Enforcement Rules

### When to Apply
Apply the Extended ICM file structure when:
- Scaffolding a new AI agent project
- Building a multi-stage pipeline or workflow
- Creating a content production system
- Setting up any project with more than 2 sequential steps
- User asks to "set up a project", "scaffold", or "create a workspace"

### Required Files — Never Skip These
1. **Root `CONTEXT.md`** — Project overview, objective, audience, stage summary, rules
2. **`ROUTER.yaml`** — Stage transition DAG. Even for linear flows, define the `next:` chain explicitly
3. **`env.example`** — Environment variable template (never `.env` with real values)
4. **Stage `CONTEXT.md`** — Every stage MUST have a contract defining: Role, Inputs, Process, Output, Constraints
5. **Stage `GATE.md`** — Every stage MUST have entry conditions and exit criteria

### Required Directories
```
workspace/
├── CONTEXT.md
├── ROUTER.yaml
├── env.example
├── stages/
│   └── NN-stage-name/
│       ├── CONTEXT.md
│       ├── GATE.md
│       ├── references/
│       ├── output/
│       └── fallback/        (for critical stages)
├── _config/
├── _tools/
├── _state/
│   ├── memory.jsonl
│   ├── variables.yaml
│   └── checkpoints/
├── _logs/
│   ├── runs/
│   └── errors/
├── shared/
├── skills/
└── setup/
    └── questionnaire.md
```

### Stage Naming
- Number stages sequentially: `01-`, `02-`, `03-`
- Parallel sub-stages use letter suffixes: `03a-`, `03b-`
- Names should be verb or noun describing the job: `01-research`, `02-analyze`, `04-review`

### CONTEXT.md Contract Format
Every stage CONTEXT.md must include these sections:
- **Role** — What the agent is in this stage (one job only)
- **Inputs** — Explicit file paths to upstream outputs
- **Process** — Numbered steps
- **Output** — What to write to `output/` and the filenames
- **Constraints** — What NOT to do

### GATE.md Format
Every GATE.md must include:
- **Entry Conditions** — Checklist of prerequisites
- **Exit Criteria** — Checklist of quality checks
- **On Failure** — What to do when the stage fails

### ROUTER.yaml Patterns
Always define transitions explicitly. Available patterns:
- `next:` — default linear path
- `branch_if:` — conditional routing
- `mode: parallel` + `sub_stages:` — concurrent execution
- `reject_to:` — feedback loops
- `max_retries:` / `max_rejections:` — loop guards
- `on_fail: fallback | skip | halt`

### Principles — Always Follow
1. **Minimal context** — Load only the current stage's CONTEXT.md
2. **Single source of truth** — Never duplicate information across stages
3. **One-way references** — Stages reference upstream outputs, never downstream
4. **One stage, one job** — A stage that researches does not also write
5. **Output as handoff** — One stage's `output/` is the next stage's input
6. **Log everything** — Token usage, cost, timing go to `_logs/runs/`
7. **State is persistent** — Cross-stage variables in `_state/variables.yaml`
