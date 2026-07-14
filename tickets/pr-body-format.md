---
type: PR Template
title: PR body format
description: The PR description skeleton — What, Why, Tests, Closes always; others when they apply.
tags: [pull-request, template]
timestamp: 2026-07-07T00:00:00Z
---

# PR body format

Every PR body uses this skeleton. `What`, `Why`, `Tests`, and `Closes` are always
present; the other sections are added only when they apply.

```markdown
## What
<The concrete change: what is added, removed, or modified.>

## Why
<The reason and the root cause — not just the symptom. Link the ADR when the
change stems from an architectural decision.>

## Scope
<Optional. Boundaries: what is explicitly out of scope, whether this is one phase
of a larger change, or work intentionally reverted.>

## Validation
<Optional but recommended. How it was verified beyond tests: production
observations, concrete logs, manual checks.>

## Tests
<Tests added or changed, full-suite status, and the project's typecheck
(e.g. `tsc --noEmit`).>

## Risk / Rollback
<Optional. For risky changes (deploys, migrations, infra): what can break and how
to roll back.>

## Breaking changes
<Optional. Call out anything that breaks compatibility: DB migrations, API changes.>

## Evidence / Screenshots
<Optional. For user-facing or visual changes.>

## Notes
<Optional. Caveats, forward references, known follow-ups.>

## Closes
<The Jira key and/or GitHub issue this closes. Follow-ups, if any.>
```

**Required vs. optional**

| Section | Required | Purpose |
| --- | --- | --- |
| What | Always | The change itself. |
| Why | Always | The reason and root cause; link the ADR if any. |
| Tests | Always (except docs-only PRs) | Shows nothing regressed. |
| Closes | Always | Ties the PR back to its ticket/issue. |
| Validation | Recommended | Verification beyond the test suite. |
| Scope | When applicable | Partial, phased, or reverted work. |
| Risk / Rollback | When applicable | Risky changes. |
| Breaking changes | When applicable | Compatibility breaks. |
| Evidence / Screenshots | When applicable | Visual / user-facing changes. |
| Notes | When applicable | Caveats and follow-ups. |

Related: [tickets & traceability](traceability.md).
