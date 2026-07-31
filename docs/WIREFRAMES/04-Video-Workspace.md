# Video Workspace Wireframe

## Feature

Feature 007 — Video Workspace Wireframe

## Purpose

The Video Workspace is the investigation page for one video.

It answers one question:

> **Why is this video performing the way it is?**

The workspace preserves the story of the video: current performance, meaningful comparisons, detected changes, creator notes, title and thumbnail history, milestones, and the evidence behind Producer observations.

## Design Rules

1. **One-screen rule** — the initial desktop view fits within 1920×1080 at 100% browser zoom without page-level vertical scrolling.
2. **Case file, not metric dump** — the screen explains the video rather than reproducing every YouTube Studio field.
3. **Evidence before explanation** — Producer may summarize only conclusions already supported by the Evidence Engine.
4. **Chronology matters** — detected and creator-entered events appear on a unified timeline.
5. **Changes are not causes by default** — title, thumbnail, traffic, or publishing events may be correlated with performance changes but must not be labeled causal without sufficient evidence.
6. **History is append-only by default** — prior titles, thumbnails, descriptions, metrics, and events remain preserved.
7. **No invented precision** — confidence and sample limitations must be visible.
8. **Read-only YouTube boundary** — v0.1 may record local notes but cannot alter the YouTube video.

## Reference Viewports

- Primary desktop: 1920×1080
- Minimum desktop: 1366×768
- Tablet: 768–1024 CSS pixels
- Mobile: 360 CSS pixels minimum

## Desktop Layout

```text
┌────────────────────────────────────────────────────────────────────────────────────────────┐
│ YT-Companion  Portfolio › Channel › Videos › I Will Never Be Too Tired   Sync ✓  Settings │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ [thumbnail]  I Will Never Be Too Tired                                                    │
│              Published yesterday · Public · 18:42 · Standard video                         │
│              Healthy early performance · Updated 8 minutes ago                             │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ PERFORMANCE                                                                                │
│ Views        CTR        Watch time      Avg duration     Comments     Subs gained   Revenue*│
│ 482          6.1%       66.2 h          8:14             37           +9            $11.42   │
│ +31% vs      -0.2pt     +22% vs         +0:41 vs         2.4×         +4 vs          +18% vs │
│ age-match    age-match  age-match       age-match        baseline     baseline       baseline│
├──────────────────────────────────────────────────────────────┬─────────────────────────────┤
│ PRODUCER FINDING                                            │ CASE SUMMARY                │
│ This video is outperforming recent uploads because viewers  │ Current title: original     │
│ are watching longer after clicking. CTR is near normal.     │ Thumbnail: version 1       │
│                                              Show evidence ›│ Traffic shift: Facebook ↑  │
│                                                             │ Notes: 1                   │
├──────────────────────────────────────────────────────────────┼─────────────────────────────┤
│ TIMELINE                                                    │ EVIDENCE SNAPSHOT           │
│ 09:00  Published                                            │ Compared with previous 3   │
│ 09:47  First comment                                        │ standard uploads at 24 h   │
│ 12:10  External traffic increased                           │                             │
│ 16:00  Retention exceeded age-matched baseline              │ Avg duration: +8.9%        │
│ 20:32  Reached 400 views                                    │ CTR: -0.2 percentage point │
│                                            Open timeline ›  │ Confidence: Moderate       │
├──────────────────────────────────────────────────────────────┴─────────────────────────────┤
│ Tabs: Overview | Performance | Timeline | Titles | Thumbnails | Notes | Related content     │
│ Snapshot healthy · Data through 1:00 PM · *Revenue available under current authorization   │
└────────────────────────────────────────────────────────────────────────────────────────────┘
```

All values are illustrative mock data.

## Initial View Structure

### Video Identity

Must show:

- Current thumbnail
- Current title
- Publication date and time
- Visibility
- Duration
- Content format
- Data freshness

Historical values do not replace current identity; they remain available in dedicated tabs.

### Performance Strip

Default metrics:

- Views
- CTR
- Watch time
- Average view duration
- Comments
- Subscribers gained
- Revenue when authorized

Every comparison must identify its baseline. New videos default to age-matched comparisons against similar-format uploads. Older videos may use selected date periods or lifetime percentile context.

### Producer Finding

The initial screen shows at most one primary finding.

A finding must include:

- Plain-language conclusion
- Comparison population
- Period or age window
- Supporting metrics
- Confidence or limitation
- Evidence link

Producer must not claim that a title or thumbnail change caused an outcome merely because the events occurred near each other.

### Case Summary

A compact factual panel showing only currently relevant state:

- Current title version
- Current thumbnail version
- Significant traffic-source change
- Creator-note count
- Detected unresolved anomaly, if any

### Timeline Preview

The preview shows up to five meaningful events. Full chronology opens separately.

Event sources include:

- YouTube publication and metadata observations
- Archived title or thumbnail changes
- Metric milestones
- Significant traffic-source changes
- Evidence Engine detections
- Local creator notes

Each event records its source and whether its timestamp is exact, snapshot-derived, or manually entered.

### Evidence Snapshot

Shows the compact proof behind the primary finding:

- Comparison group
- Sample size
- Key supporting metrics
- Confidence
- Known limitations

## Tabs

### Overview

The initial one-screen case file.

### Performance

Detailed charts, age-matched curves, traffic sources, retention, revenue, and comparison controls.

### Timeline

Complete chronological event history with filters by event type and source.

### Titles

Observed title versions, first-seen and last-seen timestamps, duration used, and performance context. v0.1 does not change titles.

### Thumbnails

Archived thumbnail versions, hashes, first-seen and last-seen timestamps, duration used, and performance context. v0.1 does not change thumbnails.

### Notes

Local creator notes. Notes may record decisions such as why a thumbnail was changed. Notes are local YT-Companion data and never write to YouTube.

### Related Content

Videos with a documented relationship, such as shared topic labels, series membership, linked Shorts, or statistically similar performance curves. Similarity must expose its matching basis.

## Evidence Engine Contract

The Video Workspace consumes findings from an Evidence Engine that owns deterministic calculations.

The Evidence Engine must return structured fields rather than prose alone:

- Finding identifier
- Finding type
- Video identifier
- Comparison group and sample size
- Metric names and values
- Calculation method
- Period or age window
- Confidence
- Limitations
- Supporting snapshot or event identifiers

Producer translates approved findings into readable language. Swapping or disabling an LLM must not change the underlying calculation.

## Change Detection

YT-Companion may detect metadata changes by comparing snapshots. Because YouTube APIs may not provide exact edit timestamps, the UI must distinguish:

- Exact timestamp
- First observed at snapshot time
- Manually entered time

A detected change must never be displayed with false timestamp precision.

## Edge States

### Newly Published

Use age-matched metrics and label unstable values as early data. Avoid strong conclusions when the sample is too small.

### Insufficient Comparison Set

Display `Collecting comparison history` and suppress unsupported Producer findings.

### Missing CTR or Retention

Show unavailable fields with the reason. Do not infer them from views or watch time.

### Deleted or Private Video

Preserve the local case file and historical observations. Clearly label the current YouTube availability state.

### Revoked Authorization

Keep previously collected history readable and show the last successful collection time. Disable claims requiring fresh data.

### Partial API Failure

Render available sections, identify stale or unavailable sections, and preserve data timestamps.

### No Timeline Events Beyond Publish

Show publication as the sole event and explain that additional events appear as snapshots and changes accumulate.

## Responsive Behavior

### Tablet

- Performance metrics wrap into two rows.
- Producer and Case Summary remain side by side when space permits.
- Timeline and Evidence stack below.

### Mobile

- Page-level vertical scrolling is allowed.
- Identity, Producer finding, and performance summary appear first.
- Tabs become a horizontally scrollable labeled tab list.
- Metric comparisons remain text-visible; meaning cannot depend on color.

## Accessibility

- All tabs and rows are keyboard reachable.
- Thumbnail includes useful alt text based on title and version context.
- Timeline uses semantic ordered-list structure.
- Confidence and status are expressed with text, not color alone.
- Focus order follows identity, performance, finding, evidence, timeline, then tabs.
- Dense data remains readable at 200% zoom through reflow.

## Performance Targets

- Cached case file shell visible within 2 seconds on LAN reference hardware.
- Large timeline and chart datasets load after the initial overview.
- Thumbnail history uses cached local assets and lazy loading outside the initial view.
- Failure of one detailed data source must not block the identity and cached summary.

## Acceptance Criteria

Feature 007 is complete when:

- The primary question is explicit.
- The initial desktop overview fits without page-level scrolling.
- Video identity, performance, one finding, timeline preview, evidence, and collection health are visible.
- Every conclusion exposes its comparison group and supporting metrics.
- Change timestamps disclose their precision.
- Title and thumbnail history are preserved without enabling YouTube edits.
- Local notes are clearly separated from YouTube data.
- New, insufficient-history, deleted/private, revoked-authorization, partial-failure, tablet, and mobile states are defined.
- No element exists solely for decoration.

## Out of Scope

- Editing titles, descriptions, visibility, tags, or thumbnails
- Uploading or scheduling content
- Automatic A/B thumbnail changes
- Causal claims based only on timing
- Free-form AI chat
- Sponsor tracking
- Social-post automation
