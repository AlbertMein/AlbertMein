---
name: debugging
description: "Structured debugging methodology. Use when investigating errors, unexpected
             behavior, or test failures. Systematic root cause analysis."
---

## Debugging Protocol

When encountering an error or unexpected behavior, follow this structured approach.
Do NOT guess-and-check randomly.

### Step 1: Reproduce
- Get the exact error message, traceback, or unexpected output
- Identify the minimal reproduction case
- Note: if you can't reproduce it, you can't fix it

### Step 2: Isolate
- Narrow down WHERE the issue is:
  - Which file? Which function? Which line?
  - Read the relevant code carefully
- Check recent changes: `git diff` and `git log --oneline -10`
- Is this a regression? Does `git stash` fix it?

### Step 3: Understand
- Read the error message literally — what is it actually saying?
- Check types, variable values, function signatures
- Read documentation for any external APIs involved
- Form a hypothesis: "I think X is happening because Y"

### Step 4: Fix
- Make the SMALLEST change that fixes the issue
- Don't refactor while debugging — fix first, clean later
- Write a test that catches this specific bug (regression test)

### Step 5: Verify
- Run the failing test — confirm it passes
- Run the full test suite — confirm nothing else broke
- Test the original reproduction case manually

### Anti-patterns to avoid
- Adding print statements everywhere without a hypothesis
- Changing multiple things at once
- "Fixing" by adding try/except that swallows errors
- Assuming the bug is in library code (it's almost always your code)
