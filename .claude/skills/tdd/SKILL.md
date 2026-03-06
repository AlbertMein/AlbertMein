---
name: tdd
description: "Use when implementing new functions, fixing bugs, or refactoring existing code.
             Use when the user says 'test', 'TDD', 'red-green', or when writing any new logic
             that could break. Enforces red-green-refactor cycle with mandatory test execution."
---

# Test-Driven Development

## Overview
Every piece of new logic gets a failing test before implementation code exists.
**Core principle:** If you didn't watch the test fail, you don't know if it tests the right thing.

**"Violating the letter of the rules is violating the spirit of the rules."**

## The Iron Law
```
NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST
```

## When to Use
- **Always:** New functions, bug fixes, refactors that change behavior
- **Sometimes:** Internal helper functions (test through their callers)
- **Never:** Config files, documentation, type-only changes

## The Process

### Phase 1: RED — Write a failing test
1. Write the minimal test that describes expected behavior
2. Run the test: `python -m pytest path/to/test.py -v`
3. **VERIFY it FAILS** — read the output, confirm the failure message
4. If it passes, your test is wrong — it's not testing the new thing

```python
def test_calculate_token_cost():
    result = calculate_token_cost(model="gpt-4", input_tokens=1000, output_tokens=500)
    assert result == 0.045
```

### Phase 2: GREEN — Write minimal code to pass
1. Write ONLY enough code to make the failing test pass
2. No optimization. No edge cases. No "while I'm here" changes.
3. Run the test: confirm it PASSES
4. **Read the full output** — don't assume success

### Phase 3: REFACTOR — Clean up while green
1. Improve readability, performance, DRY — tests must stay GREEN
2. Run tests after EVERY change
3. Add edge case tests → repeat RED-GREEN for each
4. Commit after each complete cycle

## Verification Gates (MANDATORY)
- After RED: you MUST run the test and see it FAIL
- After GREEN: you MUST run the test and see it PASS
- After REFACTOR: you MUST run ALL tests and see them PASS
- **Prohibited language:** "should work", "probably passes", "seems fine"

## Red Flags — STOP and Return to RED
If you catch yourself thinking:
- "Let me write the implementation first, then add tests"
- "This is too simple to test"
- "I'll just run the tests at the end"
- "The test would be trivial so I'll skip it"

ALL of these mean: STOP. Write the failing test FIRST.

## Common Rationalizations
| Excuse | Reality |
|--------|---------|
| "Too simple to test" | Simple code breaks. Test takes 30 seconds. |
| "I'll write tests after" | Tests written after pass immediately and prove nothing |
| "The function already works" | Then the test takes 10 seconds to write |
| "Tests slow me down" | Debugging without tests is 5x slower |
| "Just a quick fix" | Quick fixes without tests cause regressions |

## For Bug Fixes
1. Write a test that reproduces the exact bug
2. Run it — confirm it FAILS (reproduces the bug)
3. Fix with minimal change
4. Run it — confirm it PASSES
5. Run full suite — confirm no regressions

## Anti-patterns
- Writing production code then backfilling tests (tests prove nothing)
- Testing implementation details instead of behavior
- Mocking everything (test becomes meaningless)
- Skipping RED phase ("I know the test would fail")

## Announcement
Always say: "I'm using the TDD skill — starting with a failing test for [behavior]."
