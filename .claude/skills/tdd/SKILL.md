---
name: tdd
description: "Test-driven development workflow. Use when implementing new functions,
             fixing bugs, or refactoring. Enforces red-green-refactor cycle."
---

## TDD Protocol (Red-Green-Refactor)

When implementing new functionality or fixing bugs, follow this cycle:

### Step 1: RED — Write a failing test first
- Write the minimal test that describes the expected behavior
- Run the test — confirm it FAILS (this validates the test itself)
- If it passes, your test isn't testing the right thing

```python
# Example: testing a new function
def test_calculate_token_cost():
    result = calculate_token_cost(model="gpt-4", input_tokens=1000, output_tokens=500)
    assert result == 0.045  # expected cost
```

### Step 2: GREEN — Write minimal code to pass
- Write ONLY enough code to make the test pass
- Don't optimize, don't handle edge cases yet
- Run the test — confirm it PASSES

### Step 3: REFACTOR — Clean up while green
- Improve the implementation (readability, performance, DRY)
- Run tests after each change — they must stay GREEN
- Add edge case tests, then repeat the cycle for each

### Rules
- Never write production code without a failing test
- One logical change per cycle
- Commit after each green phase
- If a bug is reported, write a test that reproduces it FIRST

### For Bug Fixes
1. Write a test that reproduces the exact bug
2. Confirm the test fails
3. Fix the bug with minimal change
4. Confirm the test passes
5. Check no other tests broke
