# Producer Wireframe

## Feature

Feature 008 — Producer Wireframe

## Purpose

Producer is the evidence-driven observation screen for one channel or the full creator portfolio.

It answers one question:

> **What patterns am I missing, and what deserves investigation?**

Producer is not a chatbot, motivational feed, or free-form AI opinion page. It presents only findings that have already passed Evidence Engine rules.

## Design Rules

1. **One-screen rule** — the initial desktop view fits within 1920×1080 without page-level vertical scrolling.
2. **Evidence first** — every observation has a visible basis, sample, comparison, and limitation.
3. **No filler** — when there is nothing sufficiently meaningful, Producer says so.
4. **No causation by proximity** — timing alone does not prove that a title, thumbnail, topic, or upload decision caused a result.
5. **Plain language, exact evidence** — the summary is readable; the proof remains one action away.
6. **Deterministic core** — the Evidence Engine creates approved findings. An optional LLM may rewrite wording but cannot create or alter calculations.
7. **Action language stays proportional** — Producer may suggest investigation or consideration, not certainty or guaranteed outcomes.
8. **Historical findings remain reviewable** — findings are retained with their original evidence snapshot and later status.

## Desktop Layout

```text
┌────────────────────────────────────────────────────────────────────────────────────────────┐
│ YT-Companion  Portfolio › Growing Old w/o Growing Old › Producer   90 days ▾  Sync ✓  ⚙  │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ PRODUCER                                      What patterns am I missing?                    │
│ 3 current findings · 1 new since last visit · Updated 8 minutes ago                        │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ FILTERS:  Current  |  New  |  Confirmed  |  Watching  |  Dismissed     Topic ▾  Confidence▾│
├──────────────────────────────────────────────────────────────┬─────────────────────────────┤
│ PRIMARY FINDING                                             │ EVIDENCE SUMMARY            │
│ Family-oriented videos generated 2.8× more comments per     │ Compared: 6 family videos  │
│ 1,000 views than the channel baseline during the last       │ vs 14 other videos         │
│ 30 days.                                                    │ Metric: comments / 1K views│
│                                                             │ Difference: +180%          │
│ Confidence: High · Scope: 20 videos                         │ Limitation: small sample   │
│                              Open evidence ›  Open videos › │ Calculation details ›      │
├──────────────────────────────────────────────────────────────┼─────────────────────────────┤
│ OTHER FINDINGS                                              │ WATCHING                    │
│ 1. Curiosity titles averaged 14% higher CTR over 90 days.   │ Friday uploads may be      │
│    Moderate confidence · 12 matched videos        Evidence ›│ outperforming Monday, but  │
│                                                             │ only 4 comparable pairs    │
│ 2. Average view duration increased this week while CTR      │ exist. More data required. │
│    remained stable. High confidence               Evidence ›│                             │
├──────────────────────────────────────────────────────────────┴─────────────────────────────┤
│ History: 27 findings · 6 confirmed · 3 superseded · 2 dismissed     Open Producer history ›│
│ Evidence Engine healthy · Optional language provider: Local Ollama (available)              │
└────────────────────────────────────────────────────────────────────────────────────────────┘
```

All values are illustrative mock data.

## Finding States

- **New** — not previously viewed.
- **Current** — still supported by the latest eligible evidence.
- **Watching** — potentially meaningful but below the publication threshold.
- **Confirmed** — repeated across multiple evaluation windows or samples.
- **Superseded** — replaced by a newer finding using better or broader evidence.
- **Dismissed** — hidden by the creator but preserved in history.
- **Invalidated** — no longer supported after corrected or expanded data.

Dismissal is a local YT-Companion action and never changes YouTube.

## Required Finding Contract

Every published finding must include:

- Finding identifier and version
- Scope: portfolio, channel, video set, or individual video
- Plain-language statement
- Metric or metrics used
- Comparison population
- Evaluation period or age window
- Sample size
- Calculation method
- Effect size
- Confidence level
- Limitations
- Supporting channel and video identifiers
- Evidence creation timestamp
- Evidence Engine version
- Finding state

Producer wording is not the source of truth. The evidence record is.

## Confidence

Confidence labels must be deterministic and documented. They may consider:

- Sample size
- Effect size
- Variability
- Completeness of source data
- Number of independent comparison windows
- Stability when outliers are removed
- Match quality between compared videos

Producer must not display a numeric probability unless the statistical method genuinely supports one.

## Initial View Limits

To preserve the one-screen rule:

- One primary finding
- Up to two secondary findings
- One Watching item
- Compact evidence summary
- Historical totals only

The complete finding directory opens separately.

## Interactions

- **Open evidence** — shows calculation, sample, exclusions, and supporting records.
- **Open videos** — opens the relevant filtered video set.
- **Dismiss** — hides a finding from the current view while preserving history and rationale.
- **Mark useful / not useful** — optional local feedback for ranking, never evidence truth.
- **Change range** — reruns or selects findings valid for the chosen window.
- **Portfolio/channel switch** — changes scope without blending channel attribution.

## Empty and Insufficient-Data States

### No findings

Display:

> No evidence-backed findings require your attention right now.

This is a successful state, not an error.

### Collecting baseline

Display the exact missing requirement, such as:

> Producer needs at least 10 comparable standard videos or 30 days of snapshots before evaluating title patterns.

### No eligible comparisons

Explain why formats, ages, or data permissions prevent a fair comparison.

## Failure States

- Evidence Engine unavailable: show prior findings as cached and stale.
- Partial metric failure: withdraw findings dependent on the missing metric.
- Language provider unavailable: show deterministic template wording.
- Revoked Google authorization: retain historical findings and label freshness.
- Corrected source data: mark affected findings superseded or invalidated; never silently rewrite history.

## Optional LLM Boundary

The optional language provider receives a structured approved finding and may only:

- Improve readability
- Adjust tone within configured limits
- Summarize limitations
- Produce alternative wording

It may not:

- Add metrics
- Change values
- Change confidence
- Change scope
- Remove material limitations
- Claim causation
- create a finding from raw analytics

YT-Companion must remain fully functional with no LLM configured.

## Responsive Behavior

Desktop uses the two-column finding/evidence layout.

Tablet stacks Evidence Summary beneath the Primary Finding.

Mobile shows findings as compact sections in this order:

1. Primary finding
2. Confidence and scope
3. Evidence summary
4. Secondary findings
5. Watching
6. History and system health

Mobile may scroll; the one-screen rule applies to the initial desktop view.

## Accessibility

- Findings and states must not rely on color alone.
- Evidence actions require descriptive labels.
- Confidence and limitations must be readable by assistive technology.
- Keyboard navigation follows visual order.
- Dismissal requires confirmation and provides an undo path.

## Acceptance Criteria

- The screen explicitly answers its primary question.
- The initial desktop view fits without page-level scrolling.
- No more than four finding blocks appear initially.
- Every published finding has a complete evidence contract.
- No finding appears merely to fill space.
- No LLM is required.
- LLM output cannot alter evidence.
- Watching items are clearly distinguished from published findings.
- Corrected data preserves audit history.
- Empty, baseline, partial-failure, stale-data, revoked-authorization, tablet, and mobile states are defined.
- No YouTube write action exists.
