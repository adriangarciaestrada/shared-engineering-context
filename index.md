---
type: Index
title: Shared Engineering Context
description: Root navigation for the project-agnostic engineering knowledge bundle.
tags: [engineering, conventions, index]
timestamp: 2026-07-07T00:00:00Z
---

# Shared Engineering Context

Project-agnostic engineering conventions for both humans and AI agents. Each link
below is a self-contained concept; follow the graph from any entry point.

## Git & change flow
- [Branches](git/branches.md) — branching model and push preference.
- [Commit messages](git/commit-messages.md) — Conventional Commits.
- [Merge gating](git/merge-gating.md) — required CI checks, branch protection, dependency automation.

## Tickets & PRs
- [Tickets & traceability](tickets/traceability.md) — Jira keys, PR title rules.
- [PR body format](tickets/pr-body-format.md) — the PR description skeleton.

## Building & shipping safely
- [Secrets management](secrets.md) — never commit secrets; 1Password + `gitleaks`.
- [Code quality & pre-completion checks](code-quality.md) — the check suite, tests, edge cases.
- [Infrastructure as Code](iac.md) — Pulumi conventions and imports.
- [Security](security.md) — least privilege, scanners, threat model, DNS posture.
- [Local development & containers](local-containers.md) — containerized dev and tooling; Miniflare.

## Working conventions
- [Repo structure & documentation](repo-structure.md) — `CLAUDE.md`, `SECURITY.md`, hygiene.
- [Writing conventions](writing-conventions.md) — English, impersonal.
- [Spec / design workflow](spec-workflow.md) — OpenSpec lifecycle, acceptance criteria.

## Consolidated
- [Don'ts](donts.md) — the consolidated "what not to do" list.
- [Appendix: excluded project-specific detail](appendix.md) — audit trail.
