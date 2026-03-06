---
name: planning
description: "Use when starting any non-trivial feature, debugging session, or refactoring task.
             Use when the user says 'plan', 'break down', 'how should I approach', or when a task
             has more than 2 steps. Breaks work into ordered steps with verification gates."
---

# Structured Planning

## Overview
Every non-trivial task gets a plan before any code is written.
**Core principle:** Planning is not overhead — it prevents the 3x rework that comes from diving in blind.

**"Violating the letter of the rules is violating the spirit of the rules."**

## The Iron Law
```
NO IMPLEMENTATION WITHOUT AN APPROVED PLAN FIRST
```

## When to Use
- **Always:** Features, refactors, multi-file changes, bug investigations
- **Sometimes:** Single-file changes with non-obvious implications
- **Never:** Typo fixes, comment updates, single-line changes

## The Process

### Phase 1: Understand
1. Restate the goal in your own words — if you can't, you don't understand it
2. Identify what files/modules are involved (read them, don't assume)
3. List unknowns — what do you need to read or research first?

### Phase 2: Plan
1. Break the task into discrete, ordered steps (max 7)
2. Each step must have a clear success criteria
3. Identify dependencies between steps
4. Flag risks: breaking changes, security implications, performance
5. Estimate complexity: trivial | moderate | complex

### Phase 3: Validate (GATE — do not skip)
Before executing, confirm:
- [ ] Each step has a testable success criteria
- [ ] No step requires information you don't have yet
- [ ] Edge cases and error scenarios are addressed
- [ ] Tests are included for new logic
- [ ] Present plan to user and WAIT for approval

### Phase 4: Execute
- Work through steps sequentially
- After each step, verify it works before moving on
- If a step fails, STOP and reassess — don't push forward blindly
- If 3+ steps fail, the plan is wrong — return to Phase 1

## Red Flags — STOP and Re-plan
If you catch yourself thinking any of these, STOP:
- "I'll figure it out as I go"
- "This is simple enough to just start coding"
- "I can plan in my head, no need to write it down"
- "Let me just make this one quick change first"

ALL of these mean: STOP. Write the plan.

## Common Rationalizations
| Excuse | Reality |
|--------|---------|
| "Too simple to plan" | Simple tasks don't need 7 steps. They still need 2-3 written steps. |
| "Planning is slow" | Rework from no plan is 3x slower |
| "I already know what to do" | Then writing it down takes 30 seconds |
| "The user wants it fast" | Fast means right the first time |

## Output Format
```
## Plan: [Goal]

### Understanding
[1-2 sentences restating the problem]

### Steps
1. [Step] — success: [criteria]
2. [Step] — success: [criteria]
...

### Risks
- [Risk and mitigation]

### Complexity: [trivial|moderate|complex]
```

## Announcement
Always say: "I'm using the planning skill to break down [task]."
