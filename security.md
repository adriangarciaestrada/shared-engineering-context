---
type: Engineering Convention
title: Security
description: Append-only audit storage, pagination, graceful degradation, least privilege, scanners, DNS posture.
tags: [security, least-privilege, scanners, dns]
timestamp: 2026-07-07T00:00:00Z
---

# Security

- **Append-only evidence/audit storage** — write new objects, never overwrite. With
  timestamped keys, lexical order equals chronological order.
- **Always paginate when listing** from object stores or APIs (list calls cap results
  and signal truncation). Skipping pagination silently drops data and produces false
  positives.
- **Degrade gracefully:** a single failing check should be recorded (e.g. as `unknown`),
  never abort the whole run or throw. Best-effort collection over all-or-nothing.
- **Least privilege per route:** separate auth tokens for read-only vs. side-effecting
  endpoints; bad/missing token → 401, disallowed → 403, wrong method → 405. Optional
  IP allowlists on sensitive read endpoints.
- **Don't tie production infrastructure to personal or account-bound resources**
  (e.g. a personal `*.workers.dev` subdomain) — use org-owned domains so a lapsed
  account can't hijack it.
- **Document the threat model and its assumptions**, and re-validate them whenever the
  architecture changes (e.g. moving from static export to a server runtime reopens
  whole classes of risk).
- **Script security/pentest-readiness checks** and drop dated artifacts per run.
- **Run automated scanners** in CI and locally: `gitleaks` for secrets, `trivy`
  for image/dependency CVEs, and `semgrep` for static analysis. Pin them and run
  them containerized (see [local development & containers](local-containers.md)) so
  versions are reproducible.
- **Email/DNS posture:** progress DMARC `p=none → quarantine → reject` gated on report
  data; restrict cert issuance with CAA; disable provider features that silently
  re-inject permissive records.

Related: [secrets management](secrets.md), [merge gating](git/merge-gating.md).
