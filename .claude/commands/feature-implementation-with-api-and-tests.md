---
name: feature-implementation-with-api-and-tests
description: Workflow command scaffold for feature-implementation-with-api-and-tests in redis.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-implementation-with-api-and-tests

Use this workflow when working on **feature-implementation-with-api-and-tests** in `redis`.

## Goal

Implements a new feature or API, updating core implementation, headers, and adding or updating tests to cover the new functionality.

## Common Files

- `src/*.c`
- `src/*.h`
- `tests/unit/*.tcl`
- `tests/modules/*.c`
- `tests/modules/Makefile`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update or add implementation files in src/ (e.g., .c, .h)
- Update or add related header files in src/
- Update or add test files in tests/unit/ or tests/modules/
- Update Makefile or test infrastructure if new tests or modules are added

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.