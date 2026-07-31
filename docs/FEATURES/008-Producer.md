# Feature 008 — Producer

## Status

Design complete. No application code implemented.

## Primary Question

> **What patterns am I missing, and what deserves investigation?**

## Product Decision

Producer is an evidence presentation and prioritization layer. It is not the Evidence Engine and does not own analytical truth.

The Evidence Engine:

- Evaluates eligible data
- Applies documented comparison rules
- Produces versioned findings
- Stores calculations, samples, confidence, and limitations
- Invalidates or supersedes findings when evidence changes

Producer:

- Ranks approved findings
- Presents them in plain language
- Links to evidence and affected videos
- Preserves finding history
- Optionally uses a language provider to improve wording

## Non-Negotiable Boundary

The application must work with deterministic template wording and no configured LLM.

An LLM may not create a finding from raw analytics, modify values, alter confidence, remove material limitations, or assert causation.

## Initial View

The initial desktop view contains:

- One primary finding
- Up to two secondary findings
- One Watching item
- One compact evidence summary
- Finding-history totals
- Evidence Engine and optional language-provider health

## Data Integrity

Findings are versioned and append-only. Corrected source data does not silently overwrite old conclusions. Affected findings become superseded or invalidated with an audit trail.

## Local Actions

Dismissal and usefulness feedback are local YT-Companion actions. They affect presentation and ranking only; they do not change evidence or YouTube.

## Validation Summary

Feature 008 is valid only when:

- Every published observation is traceable to a complete evidence record.
- Insufficient evidence produces no finding.
- Watching items are clearly separated from approved findings.
- Producer remains functional without AI.
- A failed language provider falls back to deterministic wording.
- No YouTube write capability is introduced.
