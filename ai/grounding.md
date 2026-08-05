---
type: Engineering Convention
title: Grounding & context
description: Agents read the project's source of truth before generating; minimal viable RAG; context is the first suspect.
tags: [ai, agents, rag, context]
timestamp: 2026-08-04T00:00:00Z
---

# Grounding & context

- **Ground before generating.** Without project data, output is the average of the
  model's training data — generic. Agents read the project's own material before
  writing.
- **Prefer minimal viable RAG.** RAG (Retrieval-Augmented Generation) means the
  agent fetches only the relevant fragments of a corpus before generating, instead
  of receiving the whole corpus in the prompt. If the corpus fits the context
  window, a folder of markdown the agent can read *is* the retrieval system; add
  embeddings (numeric text representations that enable search by semantic
  similarity) only at scale.
- **Select context per task.** Load only the material relevant to the request, not
  the whole corpus.
- **Keep one shared source of truth.** All agents read the same canonical
  repository: fewer hallucinations, fewer cross-agent inconsistencies, and updates
  are inherited automatically. (This bundle is itself such a source.)
- **Read state before writing.** Agents parse what exists before modifying it.
- **Perception determines action.** What the agent sees conditions what it decides —
  when behavior looks wrong, audit the provided context first.
- **Manage memory proactively in long sessions.** Compress resolved work into
  summaries that preserve key decisions; archive closed items out of active
  context, retrievable on demand.

Related: [output contracts](output-contracts.md),
[repo structure & documentation](../repo-structure.md).
