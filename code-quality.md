---
type: Engineering Convention
title: Code quality & pre-completion checks
description: Run the full check suite before done; zero warnings; tests and edge cases against the real schema.
tags: [quality, tests, typecheck, lint]
timestamp: 2026-07-07T00:00:00Z
---

# Code quality & pre-completion checks

- **Run the full check suite at the end of every task** before considering it done —
  typically tests + build + typecheck (and formatter + linter for compiled languages).
- **Zero warnings and zero type errors before committing.** Treat linter warnings as
  errors (`-D warnings`).
- **Always run the formatter before committing** to avoid CI failures.
- **Remove unused imports, variables, and dead code.** Keep imports organized.
- Use modern language idioms (e.g. inline format-string interpolation).
- **All tests must pass.** Fix or remove broken test files — never leave them.
- **Cover the edge cases explicitly** and validate against the real schema/contract,
  not a hand-rolled copy: valid input, malformed/partial, empty collections, `null`
  fields, duplicates, and missing metadata.
- Where **no test suite exists**, the typecheck is the verification step — state that
  explicitly so contributors know what "verified" means.
- When a value is **duplicated across multiple files**, change all copies together
  (and document that they must stay in sync). The same applies to a schedule and the
  code logic that depends on it.

Related: [merge gating](git/merge-gating.md), [spec / design workflow](spec-workflow.md).
