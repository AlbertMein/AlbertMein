---
name: debugging
description: "Use when investigating errors, unexpected behavior, test failures, or crashes.
             Use when the user says 'bug', 'error', 'broken', 'not working', 'fails', or when
             tests fail unexpectedly. Systematic root cause analysis — no guessing."
---

# Systematic Debugging

## Overview
Every bug gets a root cause investigation before any fix is attempted.
**Core principle:** Systematic debugging is FASTER than guess-and-check, even when you think you know the answer.

**"Violating the letter of the rules is violating the spirit of the rules."**

## The Iron Law
```
NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST
```

## When to Use
- **Always:** Errors, test failures, unexpected behavior, crashes
- **Sometimes:** Performance issues (profile first, then debug)
- **Never:** Known issues with documented fixes

## The Process

### Phase 1: Reproduce
1. Get the exact error message, traceback, or unexpected output
2. Find the minimal reproduction case
3. **If you can't reproduce it, you can't fix it** — investigate environment differences
4. Write down the reproduction steps

### Phase 2: Isolate
1. Narrow down: which file → which function → which line?
2. Read the relevant code carefully (don't skim)
3. Check recent changes: `git diff` and `git log --oneline -10`
4. Is this a regression? Does reverting recent changes fix it?
5. Check types, variable values, function signatures at the failure point

### Phase 3: Understand — Form a Hypothesis
1. Read the error message literally — what is it actually saying?
2. Read documentation for any external APIs involved
3. Form ONE specific hypothesis: "X happens because Y at line Z"
4. **Write the hypothesis down before attempting any fix**

### Phase 4: Fix — Smallest Change Possible
1. Make the SMALLEST change that addresses the root cause
2. Don't refactor while debugging — fix first, clean later
3. Write a regression test that catches this specific bug (TDD RED phase)
4. If the fix doesn't work → new hypothesis, don't iterate on the wrong one

### Phase 5: Verify
1. Run the regression test — confirm it passes
2. Run the full test suite — confirm nothing else broke
3. Test the original reproduction case
4. **Read the full output** — don't assume

## Escalation Rule
**If 3+ fix attempts fail → the architecture is wrong.**
Stop patching. Discuss the architectural issue with the user.

## Red Flags — STOP and Return to Phase 1
If you catch yourself thinking:
- "Quick fix for now, investigate later"
- "Just try changing X and see if it works"
- "It's probably X, let me fix that"
- "Let me add a try/except to handle this"
- "Works on my end, must be environmental"

ALL of these mean: STOP. Return to Phase 1.

## Common Rationalizations
| Excuse | Reality |
|--------|---------|
| "I know what the bug is" | Then proving it takes 60 seconds |
| "Emergency, no time for process" | Systematic is FASTER than thrashing |
| "Just need to add error handling" | Error handling hides bugs, doesn't fix them |
| "The fix is obvious" | Obvious fixes that skip investigation cause new bugs |
| "Let me try one thing first" | That's guess-and-check. Investigate first. |

## Anti-patterns
- Adding print statements everywhere without a hypothesis
- Changing multiple things at once
- "Fixing" by adding try/except that swallows errors
- Assuming the bug is in library code (it's almost always your code)
- Googling the error message before reading your own code

## Announcement
Always say: "I'm using the debugging skill to investigate [error/issue]."
