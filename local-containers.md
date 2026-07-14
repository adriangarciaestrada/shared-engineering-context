---
type: Engineering Convention
title: Local development & containers
description: Develop in containers with port binds; run tooling containerized; use Miniflare for Cloudflare.
tags: [containers, docker, miniflare, local-dev]
timestamp: 2026-07-07T00:00:00Z
---

# Local development & containers

> Aspirational — not yet adopted org-wide, but recommended for new projects.

- **Develop in containers, not against the host.** Ship a `Dockerfile` and/or
  `docker-compose.yml` with each project so local dev matches CI/prod and doesn't
  depend on host-installed toolchains.
- **Bind ports from the container** rather than running services directly on the
  host machine, keeping the dev environment isolated and reproducible.
- **Run tooling in containers too** — security/static-analysis tools like `trivy`,
  `semgrep`, and `gitleaks` should run pinned via their images instead of relying
  on locally-installed versions.
- **For Cloudflare, develop locally with Miniflare** (the local Workers runtime)
  rather than hitting deployed resources.

Related: [security](security.md), [merge gating](git/merge-gating.md).
