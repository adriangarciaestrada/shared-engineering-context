---
type: Reference
title: Appendix — excluded as project-specific
description: Audit trail of detail deliberately kept out of the agnostic bundle, and why.
tags: [appendix, audit, scope]
timestamp: 2026-07-07T00:00:00Z
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
