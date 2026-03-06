---
name: planning
description: "Structured task decomposition. Use when starting any non-trivial feature,
             debugging session, or refactoring task. Breaks work into ordered steps."
---

## Planning Protocol

Before writing ANY code, follow this structured approach:

### Phase 1: Understand
1. Restate the goal in your own words
2. Identify what files/modules are involved
3. List unknowns — what do you need to read or research first?

### Phase 2: Plan
1. Break the task into discrete, ordered steps (max 7)
2. Identify dependencies between steps
3. Flag any risks (breaking changes, security implications, performance)
4. Estimate complexity: trivial | moderate | complex

### Phase 3: Validate
Before executing, confirm:
- [ ] Each step has a clear success criteria
- [ ] No step requires information you don't have
- [ ] The plan handles edge cases and error scenarios
- [ ] Tests are included for new logic

### Phase 4: Execute
- Work through steps sequentially
- After each step, verify it works before moving on
- If a step fails, stop and reassess — don't push forward blindly

### Output Format
```
## Plan: [Goal]

### Understanding
[1-2 sentences restating the problem]

### Steps
1. [Step] — [success criteria]
2. [Step] — [success criteria]
...

### Risks
- [Risk and mitigation]

### Complexity: [trivial|moderate|complex]
```
