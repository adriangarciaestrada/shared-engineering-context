# Shared Engineering Context — OKF bundle

Project-agnostic engineering conventions, practices, and don'ts — distilled from
every `CLAUDE.md` across the organization, plus the team's own working rules.
Written to be read by both humans and AI agents: per-repo `CLAUDE.md` files can
link to a concept here instead of repeating the rules.

## Format

This repository is an [Open Knowledge Format (OKF) v0.1](https://cloud.google.com/blog/products/data-analytics/how-the-open-knowledge-format-can-improve-data-sharing)
bundle: a directory of markdown files, one per **concept**, each with YAML
frontmatter (minimum required field: `type`) and a markdown body. Concepts link
to each other with standard markdown links, forming a knowledge graph an agent
can traverse. No SDK or runtime is required to produce or consume it.

- Start at [`index.md`](index.md) for progressive disclosure of every concept.
- Change history lives in [`log.md`](log.md).
- Standalone concepts live at the repository root; when a theme splits into
  several sibling concepts (e.g. `git/`, `tickets/`, `ai/`), they share a folder
  with an `index.md` navigation node of their own.

### Concept types used in this bundle

| `type` | Meaning |
| --- | --- |
| `Engineering Convention` | A house rule or practice contributors must follow. |
| `PR Template` | A reusable authoring skeleton. |
| `Reference` | Background/audit material, not a rule to follow. |
| `Index` | Navigation node (progressive disclosure). |

### Frontmatter fields

`type` (required) plus the OKF optional fields where meaningful: `title`,
`description`, `tags`, `timestamp` (ISO 8601), and `resource` (a URL/reference to
an external source of truth).

## Scope note

Org-standard tools (1Password, Cloudflare, Pulumi, Jira, OpenSpec, Wrangler,
Miniflare, gitleaks) are kept by name as the house standard. Project-specific
details (IPs, hostnames, vault/item names, ticket prefixes, stack versions,
business context) were removed — see [`appendix.md`](appendix.md) for what was
excluded and why.
