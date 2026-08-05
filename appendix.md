---
type: Reference
title: Appendix — excluded as project-specific
description: Audit trail of detail deliberately kept out of the agnostic bundle, and why.
tags: [appendix, audit, scope]
timestamp: 2026-08-04T00:00:00Z
---

# Appendix — excluded as project-specific (NOT in the agnostic bundle)

Listed so the exclusions can be audited and nothing reusable is dropped by mistake.
Each item is tied to one concrete project and would not transfer to a different repo
as-is.

- **Concrete infrastructure identifiers:** server IPs, SSH key filenames, droplet deploy
  paths, regions, hostnames/domains, zone IDs, account IDs, R2 bucket names, cron
  expressions.
- **Exact ticket prefixes and numbers** (the *practice* "reference a Jira ticket" was
  kept and generalized; the specific prefixes were not).
- **Named 1Password vault and item entries** (the *practice* "use 1Password via `op`"
  was kept; the specific vault/item names were not).
- **Per-stack tooling, versions, and commands:** specific frameworks and their versions,
  and the exact `npm`/CLI commands of each project (each repo keeps its own).
- **Business/domain context:** tenants, clients, product catalogs, launch phases.
- **Implementation-detail tricks bound to one stack:** framework token mismatches,
  icon-ordering workarounds, CMS-specific gotchas, dev-server race fixes, GraphQL
  space IDs and endpoints.
- **Per-project hosting/edge topology** (which CDN, origin bucket, build pipeline).

> Audit tip: skim this list and ask "is any of these actually a *general rule* in
> disguise?" If yes, it should move up into the bundle as a generalized concept.

## Working with AI family — pre-publication review record (2026-08-04)

The [Working with AI](ai/index.md) family was mapped against its source material
(nine course-session extracts, 192 claims) and stress-tested with an adversarial
multi-agent review before publication. Twenty candidate gaps were raised: one was
confirmed and merged (provider portability), one was initially refuted and later
reinstated on re-review (the AI contract — QA-stage rules are not a design
boundary), and eighteen were deliberately excluded. Recorded so future reviewers
do not re-derive the same candidates:

- **Self-evaluation vs. generator ≠ evaluator** — no contradiction: self-checks
  run against measurable rule sets; independent judgment remains the exit gate.
- **Containerized agent components** — covered by the unpinned-tooling rule; a
  reachability stub was added in [human oversight](ai/human-oversight.md).
- **"Amplification" framing for legitimate AI use** — the operative test is the
  minimal-mechanism ladder in [scoping](ai/scoping.md); the label adds nothing.
- **Format enumeration (JSON vs. CSV vs. plain text)** — consumer-driven format
  is the substance of [output contracts](ai/output-contracts.md); enumerations
  are implementation detail.
- **Combinatorial explosion of scripted automation** — encoded in the escalation
  ladder and the silent-failure rule.
- **Industry-case economic framing (AI as force multiplier)** — reference
  material, not a convention; business context is out of scope for this bundle.
- **End-to-end pipeline mapping before building** — composed of typed I/O
  contracts, the translation layer, and atomic decomposition.
- **Document rigor as necessary-but-not-sufficient** — function carried by "the
  deliverable outranks the pipeline".
- **One-sentence-per-pillar readiness checkpoint** — function carried by the
  vagueness detector and the clarity test.
- **Core-rule consistency evaluation before building** — carried by shift-left
  validation and adversarial critics.
- **A unified scope red-flags checklist** — both flags exist in their thematic
  files; consolidation judged unnecessary.
- **Corrections proposed, not just flagged** — literal in "the error and its fix
  shown, not asserted".
- **Capability-matched delegation** — carried by cognitive-depth matching and
  non-overlapping roles.
- **No exemption for mature commercial tools** — the no-unevaluated-output rule
  admits no vendor exception; adding emphasis would be anecdote.
- **Current state as an explicit prioritization factor** — structural input of
  gap analysis and the rescan loop.
- **Executable acceptance criteria ("must run")** — carried by the minimum-bar
  and don't-mock rules.
- **Map-to-known-practices as a stated meta-rule** — enacted throughout (GER =
  TDD, adversarial QA, staging as review) rather than stated once.
- **Builder/Critic "quality emerges from dialogue"** — prescribed piece by piece
  across the GER loop, adversarial critics, and error feedback.

> Method caveats, recorded for honesty: the refuting reviewer was instructed to
> default to refute, and no negative controls were run, so the refutation rate is
> not a calibrated measurement; the headline coverage figure (164/192 claims
> covered) is an unaudited single-rater count. One refutation in twenty was
> overturned on spot-check.
