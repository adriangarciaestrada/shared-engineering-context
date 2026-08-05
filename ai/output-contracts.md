---
type: Engineering Convention
title: AI output contracts
description: Define agents by their output format; typed I/O, forced structure, hard constraints, validation metadata.
tags: [ai, agents, schema, structured-output]
timestamp: 2026-08-04T00:00:00Z
---

# AI output contracts

- **Define an agent by its output format, not by "vibe".** An agent described by
  personality or intent instead of the concrete artifact it produces is a red flag —
  the schema is what makes it verifiable.
- **Write typed I/O contracts**: field names, types, nesting, and limits (length,
  tone, ranges) for both inputs and outputs.
- **Force the format explicitly.** LLMs default to prose, and filler breaks parsers:
  "Respond ONLY with valid JSON. No explanations. No markdown. No preamble."
- **Never assume parseable output.** Every structured-output prompt is followed by a
  downstream validator before any other system consumes the result. This file owns
  the format-validation rule; [validation](validation.md), [failure
  handling](failure-handling.md), and the don'ts list reference it rather than
  restating it.
- **Use structured messages between agents.** Schema-checked handoffs prevent
  context from being silently misread or dropped; isolate payloads to avoid
  cross-contaminating shared state.
- **Set hard constraints early.** The contract covers not only what the agent
  produces but what it must never do (files not to touch, actions not to take) —
  declared before the first run.
- **Use structured output as a vagueness detector.** If an agent cannot produce a
  structured spec from a description, the description is too vague to build from.
- **Carry validation metadata in the output** (e.g. a `verified` flag) so it is
  auditable which gate each artifact passed — written by the validator or
  independent evaluator after the gate passes, never by the agent that produced
  the artifact, and trusted by consumers only when it comes from that layer.
- **Expect a translation layer.** Even when producer and consumer both "speak
  JSON", their schemas rarely match — budget the conversion-and-validation script
  as a component in its own right.

Related: [validation](validation.md), [grounding & context](grounding.md).
