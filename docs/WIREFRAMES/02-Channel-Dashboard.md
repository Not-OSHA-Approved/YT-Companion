# Channel Dashboard Wireframe

## Feature

Feature 005 — Channel Dashboard Wireframe

## Purpose

The Channel Dashboard is the first screen shown after a creator selects a channel from the Portfolio Overview.

It answers one question:

> **What should I know about this channel today?**

The screen must summarize current performance, identify meaningful changes, and provide direct paths to deeper evidence without becoming a miniature copy of YouTube Studio.

## Design Rules

1. **One-screen rule** — the complete initial desktop view must fit within a 1920×1080 display at 100% browser zoom without page-level vertical scrolling.
2. **Overview first; details on demand** — the initial view contains only decision-relevant information.
3. **Polish, not fluff** — no decorative charts, animated counters, celebratory effects, or unsupported status language.
4. **Producer leads with meaning** — plain-language observations appear before detailed analysis.
5. **Evidence is one action away** — every Producer statement and trend indicator must link to its source metrics and calculation.
6. **Comparisons require context** — changes must name the comparison period and never imply causation without evidence.
7. **Unavailable means unavailable** — missing revenue, CTR, retention, or realtime data must be labeled rather than estimated.
8. **Channel identity remains obvious** — the selected channel and date range must remain visible at all times.

## Reference Viewports

- Primary desktop: 1920×1080 at 100% browser zoom
- Minimum desktop target: 1366×768
- Tablet: 768–1024 CSS pixels wide
- Mobile: 360 CSS pixels wide minimum

At smaller desktop sizes, labels may shorten and secondary text may collapse, but the selected channel, Producer summary, core metrics, recent-upload status, and collection health must remain visible without page-level vertical scrolling.

## Desktop Layout

```text
┌────────────────────────────────────────────────────────────────────────────────────────────┐
│ YT-Companion   Portfolio › Growing Old w/o Growing Old      28 days ▾   Sync ✓   Settings │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ GROWING OLD W/O GROWING OLD                    What should I know about this channel today? │
│ Healthy · Last upload yesterday                                  Updated 8 minutes ago       │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ TODAY AT A GLANCE                                                                          │
│ Subscribers      Views             Watch time        Revenue*          CTR      Avg duration │
│ 3,640             18,420            1,284 h           $412.38           6.2%     8:14         │
│ +18 vs prior      +12% vs prior     +9% vs prior      +6% vs prior      -0.3pt   +0:22        │
├──────────────────────────────────────────────────────────────┬─────────────────────────────┤
│ PRODUCER NOTICED                                            │ TOP MOVERS                  │
│ The newest family video is off to a stronger start than     │ ↑ Fastest start            │
│ the previous three uploads, driven by higher early watch    │   I Will Never Be Too Tired│
│ time rather than higher CTR.                                │   +31% 24-hour views        │
│                                              Show evidence ›│                             │
│                                                             │ ↓ Needs attention           │
│                                                             │   Recent shopping upload    │
│                                                             │   CTR 1.1pt below baseline  │
├──────────────────────────────────────────────────────────────┼─────────────────────────────┤
│ RECENT UPLOADS                                              │ 28-DAY TREND                │
│ Thumbnail  Title                         Age   Views  Trend  │ Views  ─╮ ╭──╮              │
│ [image]    I Will Never Be Too Tired    1d     482    ↑     │ Subs   ───╮  ╰─             │
│ [image]    Previous Upload              5d     621    →     │ Watch  ─╮ ╰──╮              │
│ [image]    Earlier Upload              10d     903    ↓     │          Open analytics ›   │
├──────────────────────────────────────────────────────────────┴─────────────────────────────┤
│ Snapshot healthy · Data through 1:00 PM · Next collection 11:00 PM · *Revenue permission ✓ │
└────────────────────────────────────────────────────────────────────────────────────────────┘
```

The values above are illustrative mock data and are not claims about any real channel.

## Information Hierarchy

### 1. Header and Channel Context

The header contains:

- Link back to Portfolio
- Selected channel name
- Date-range selector
- Synchronization state
- Settings access

The selected channel must never rely on color or a thumbnail alone for identification.

### 2. Channel Summary

The summary line contains only:

- Channel name
- Computed or explicitly known channel state
- Last upload time
- Last successful data refresh

A channel state must not be shown when the required data is incomplete. Use `Status unavailable` instead.

### 3. Today at a Glance

The default metric row contains:

- Subscribers
- Views
- Watch time
- Revenue, when authorized and available
- Impressions click-through rate
- Average view duration

Each metric includes:

- Current-period value
- Comparison to the immediately preceding equal-length period
- Unit and direction
- Accessible text equivalent for direction

Comparison examples:

- `+12% vs prior 28 days`
- `-0.3 percentage points vs prior 28 days`
- `No prior-period data`

Subscriber totals may be current totals while the comparison represents net change. Labels must make that distinction clear.

Revenue must not appear as zero when permission or monetization data is unavailable. Display `Unavailable` with an explanation path.

### 4. Producer Noticed

The dashboard shows one primary Producer observation.

The observation must:

- State what changed or what pattern was detected
- Name the relevant period or sample
- Avoid motivational filler
- Avoid causal claims unless the data supports them
- Provide `Show evidence`

When no defensible observation exists, show:

> No meaningful change detected in the selected period.

That is preferable to manufacturing an insight.

### 5. Top Movers

Top Movers contains no more than two items:

- Strongest meaningful positive movement
- Most important item needing attention

Possible subjects include:

- Recent upload early performance
- CTR change
- Watch-time change
- Subscriber contribution
- Traffic-source movement

A movement must pass a minimum significance threshold defined by the analytics feature before display. Small numerical noise does not qualify.

### 6. Recent Uploads

The initial view shows the three most recent public uploads.

Each row contains:

- Thumbnail
- Current title
- Published age or date
- Views in the selected comparison context
- Compact trend label

Selecting a row opens the future Video Workspace directly.

If fewer than three uploads exist, the space remains compact rather than filling with placeholders.

### 7. Historical Trend

The initial trend region shows compact, non-interactive summary traces for:

- Views
- Subscribers
- Watch time

These traces communicate direction only. Exact values, filters, tooltips, and comparisons belong in Analytics.

The summary traces must include accessible textual equivalents such as `Views increased 12% over the prior period`.

### 8. Collection Health

A quiet footer shows:

- Snapshot health
- Latest complete data timestamp
- Next scheduled collection
- Revenue-permission state when relevant

Warnings become prominent only when action is required.

## Date Range Behavior

Default range: `28 days`.

Supported initial choices:

- 7 days
- 28 days
- 90 days
- 365 days
- Custom

Changing the range updates every comparison-capable section consistently. A section may state that a metric is only available for a different supported interval rather than silently using a mismatched period.

## Interaction Model

- Portfolio breadcrumb returns to the Portfolio Overview.
- Date range updates the whole dashboard.
- Metric selection opens Analytics focused on that metric.
- `Show evidence` opens Producer evidence for the exact observation.
- Top Mover selection opens the relevant video or analytics evidence.
- Recent-upload selection opens that video's workspace.
- `Open analytics` opens the detailed Analytics screen using the current channel and date range.
- Sync status opens collection history and failures; it does not trigger an unconfirmed write to YouTube.

## Pre-Launch Channel State

A connected channel with no public uploads uses a purpose-built pre-launch dashboard rather than six empty metric cards.

```text
Channel connected · Pre-launch

No public uploads yet.
YT-Companion is ready to begin tracking when the first video is published.

Authorization healthy        Channel metadata collected        Snapshot schedule active
```

The dashboard must not pressure the creator to publish or invent advice without data.

## Dormant Channel State

Dormant channels keep historical metrics visible and clearly state the age of the latest upload. Producer may identify sustained inactivity only as a fact, not as a judgment.

Example:

> No public upload has been detected in 143 days.

It must not say `You should upload now` unless a future recommendation feature has explicit evidence and the user has enabled recommendations.

## Empty, Loading, and Error States

### Loading

- Preserve final layout dimensions to prevent major movement.
- Use quiet skeleton blocks.
- Show the selected channel name as soon as known.
- Do not display fabricated temporary values.

### Partial Data

- Render available sections.
- Mark affected metrics as `Unavailable` or `Delayed`.
- State which API or collection failed.
- Keep cached values labeled with their timestamp.

### Total Failure

Show:

- Clear failure summary
- Last known successful data timestamp, if available
- Retry action
- Link to connection or collection diagnostics

Do not replace a failure with zeros.

### Authorization Revoked

Show historical stored data in read-only mode with a prominent but calm notice:

> YouTube authorization needs attention. Stored history remains available, but new data cannot be collected.

### No Historical Comparison

Use `Collecting baseline` and state how much data is available. Do not compute misleading percentages from an inadequate sample.

## Responsive Behavior

### Tablet

- Metric row becomes two compact rows.
- Producer remains above Top Movers.
- Recent Uploads and Trend become tabs within the same initial viewport.
- No page-level vertical scrolling in landscape orientation at the reference tablet size when browser chrome permits.

### Mobile

The mobile initial view prioritizes:

1. Channel identity and sync health
2. Producer observation
3. Subscribers, views, and watch time
4. Recent upload status
5. Navigation to remaining metrics and details

Mobile may use vertical scrolling because forcing a desktop-density rule onto a narrow screen would reduce readability and accessibility.

Revenue, CTR, average duration, Top Movers, and trend details remain available through `More metrics` and section tabs.

## Accessibility

- Keyboard users can reach every interactive element in logical order.
- Focus states are clearly visible.
- Trend arrows include text labels.
- Color is never the sole indicator of performance.
- Thumbnails use meaningful alt text based on video title or are marked decorative when adjacent text is sufficient.
- Metric changes announce value, unit, direction, and comparison period.
- Compact trend graphics have textual summaries.
- Touch targets meet minimum accessible sizing.
- Motion is unnecessary for understanding the page.

## Performance Expectations

- Cached dashboard summary target: visible within 1 second on the LAN reference deployment.
- Full initial dashboard target: usable within 2 seconds on the LAN reference deployment.
- Slow analytics sections must not block channel identity, cached summary values, or error information.
- Thumbnail loading must use bounded dimensions and must not cause layout shifts.

These are design targets to be tested when application code exists.

## Data Required

The dashboard contract requires, when authorized and available:

- Channel metadata
- Current subscriber total
- Period views
- Period watch time
- Period estimated revenue
- Period impressions CTR
- Period average view duration
- Prior equal-length comparison values
- Three most recent public uploads
- Early-performance baselines for recent uploads
- Compact historical series for views, subscriber changes, and watch time
- Producer observation plus evidence reference
- Latest snapshot and collection-health metadata

No unavailable metric may be inferred from unrelated fields.

## Explicitly Out of Scope

- Editing channel metadata
- Uploading or scheduling videos
- Changing titles or thumbnails
- AI chat
- Decorative live counters
- Full traffic-source tables
- Full audience-retention curves
- Comment management
- Revenue forecasting
- Recommendations unsupported by collected evidence

## Acceptance Criteria

Feature 005 is complete when:

- The primary question is explicit.
- The initial 1920×1080 desktop view fits without page-level vertical scrolling.
- The 1366×768 layout retains the channel identity, Producer summary, core metrics, recent-upload status, and collection health.
- Exactly one primary Producer observation appears.
- Every insight and movement has an evidence path.
- Metrics identify their comparison period.
- Missing permission or data is never represented as zero.
- Pre-launch, dormant, loading, partial-failure, total-failure, revoked-authorization, and insufficient-history states are defined.
- Mobile behavior prioritizes readability over the desktop no-scroll rule.
- No element exists only because it looks attractive.
- The screen remains strictly read-only.

## Future Considerations

These are not part of this feature:

- User-configurable dashboard modules
- Multiple simultaneous comparison periods
- Realtime minute-by-minute panels
- Recommendation dismissal or feedback
- AI-generated narrative summaries
- Custom metric formulas

Future changes must preserve the primary question and follow the same design, test, validation, and documentation workflow.
