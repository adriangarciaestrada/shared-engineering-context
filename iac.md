---
type: Engineering Convention
title: Infrastructure as Code (IaC)
description: One entry point, getStack dispatch, snapshot before apply, Pulumi over Wrangler for Cloudflare.
tags: [iac, pulumi, cloudflare]
timestamp: 2026-07-07T00:00:00Z
---

# Infrastructure as Code (IaC)

- **One entry point (`index.ts`), no nested constructs** — keep all resources in one place.
- **Dispatch environments via a `getStack()` switch** (e.g. a `prodStack()` function).
- **Match sibling projects' house style** when adding resources, so all IaC repos read
  the same way.
- **Snapshot before every apply:** export both the IaC state and a raw provider dump so
  a rollback is always possible.
- **Document intentional exclusions from IaC** (e.g. provider-rotated keys that would
  cause predictable drift if imported) and explain why.
- No build step where the tool runs the source directly (e.g. Pulumi via ts-node).
- **Prefer Pulumi (IaC) over imperative Wrangler/CLI for Cloudflare resources.**
  Before reaching for `wrangler`, consider managing Cloudflare declaratively through
  Pulumi and **importing existing resources** into the stack, so the live state stays
  in code rather than configured ad-hoc.

Related: [secrets management](secrets.md), [security](security.md).
