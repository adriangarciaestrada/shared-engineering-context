---
type: Engineering Convention
title: Secrets management
description: Never commit secrets; store in 1Password, scan with gitleaks, encrypt in IaC config.
tags: [secrets, security, 1password, gitleaks]
timestamp: 2026-07-07T00:00:00Z
---

# Secrets management

- **Never commit secrets:** credentials, API keys, tokens, DB connection strings,
  private keys, certificates, or sensitive config files.
- **Store secrets in a password manager (1Password)** and retrieve them at runtime
  via the `op` CLI. Prefer **environment variables** over committed config files.
- **Always check `.gitignore` before committing** any new config file, and review
  the diff before pushing to make sure no secret slipped in.
- **Scan for secrets with `gitleaks`** before pushing — ideally as a pre-commit
  hook and in CI — to catch credentials that slipped past manual review.
- Provide **template files** (e.g. `config.template.json`) that document structure
  **without** real values.
- For IaC, keep secrets **encrypted in the stack config** (`pulumi config set --secret`,
  `config.requireSecret()`); never in plaintext.
- **IDs that are not secrets** (zone IDs, account IDs, domain names) may be hardcoded —
  but mark them with an explicit `// not a secret` comment so intent is clear.
- Know your **public-by-design** credentials (e.g. a read-only, published-content CMS
  delivery token bundled into client JS). Treat them as public, and **never** swap
  them for a higher-privilege (management/preview) token.
- **If a secret is committed by accident:** gitignore it, `git rm --cached <file>`,
  rewrite history to purge it, and force-push. Then rotate the secret.

Related: [merge gating](git/merge-gating.md), [security](security.md),
[infrastructure as code](iac.md).
