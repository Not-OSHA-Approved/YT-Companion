# Videos Screen Wireframe

## Feature

Feature 006 — Videos Screen Wireframe

## Purpose

The Videos screen helps a creator identify which uploads are succeeding, struggling, or changing direction.

It answers one question:

> **Which videos deserve my attention right now?**

This screen is not a complete video archive dumped into a table. It is a focused comparison surface that highlights meaningful performance differences and provides a direct path into each video's workspace.

## Design Rules

1. **One-screen rule** — the complete initial desktop view must fit within a 1920×1080 display at 100% browser zoom without page-level vertical scrolling.
2. **Rows over cards** — videos use compact rows for scanning, sorting, filtering, and comparison.
3. **Attention before chronology** — the default view prioritizes videos that are outperforming, underperforming, or changing direction rather than merely showing newest first.
4. **Fair comparisons only** — a new upload must be compared with videos at a similar age or against an explicitly named baseline.
5. **No mystery scores** — v0.1 must not display an unexplained AI score or composite quality score.
6. **Unavailable means unavailable** — missing CTR, retention, revenue, or realtime data must be labeled rather than shown as zero.
7. **One click opens context** — selecting a row opens the corresponding Video Workspace.
8. **Polish, not fluff** — thumbnails, icons, and trend markers must improve recognition or interpretation.

## Reference Viewports

- Primary desktop: 1920×1080 at 100% browser zoom
- Minimum desktop target: 1366×768
- Tablet: 768–1024 CSS pixels wide
- Mobile: 360 CSS pixels wide minimum

At the minimum desktop target, less important columns may collapse into a compact details control, but the title, age, views, watch time or average duration, CTR availability, and attention reason must remain visible.

## Desktop Layout

```text
┌────────────────────────────────────────────────────────────────────────────────────────────┐
│ YT-Companion   Portfolio › Growing Old w/o Growing Old › Videos   28 days ▾   Sync ✓   ⚙ │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ VIDEOS                                      Which videos deserve my attention right now?    │
│ 143 published · Data updated 8 minutes ago                                               │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ Search videos...      Filter: Needs attention ▾      Sort: Priority ▾      Columns ▾      │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ THUMB  TITLE                         AGE   VIEWS   CTR    AVG VIEW   WATCH TIME   WHY NOW   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ [img]  I Will Never Be Too Tired     1d     482   6.1%      8:42       69.9 h    Fast start│
│        +31% 24-hour views vs previous 3 uploads                          Open workspace ›   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ [img]  Recent Shopping Video         4d     611   3.8%      6:14       63.5 h    Low CTR   │
│        CTR is 1.1 points below its age-adjusted channel baseline          Open workspace ›   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ [img]  Driving Chat                  9d   1,204   5.9%      9:18      186.6 h    Watch time│
│        Average view duration is 18% above the 90-day channel average      Open workspace ›   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ [img]  Family Update                16d   1,481   6.4%      8:57      220.9 h    Comments  │
│        Comments per 1,000 views are 2.3× the channel baseline             Open workspace ›   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ [img]  Older Upload                 31d     893    —        7:02      104.7 h    Stable    │
│        CTR unavailable for selected period                                Open workspace ›   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ Showing 5 priority videos                    View all 143 videos ›     Export not in v0.1    │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ Snapshot healthy · Comparisons use age-matched or explicitly named baselines               │
└────────────────────────────────────────────────────────────────────────────────────────────┘
```

All values are illustrative mock data and are not claims about any real channel.

## Information Hierarchy

### 1. Channel Context

The header keeps visible:

- Portfolio breadcrumb
- Selected channel
- Current section
- Date range
- Synchronization health
- Settings access

Changing the date range updates eligible metrics and comparisons. It must not silently change the age-matching rules used for recent uploads.

### 2. Page Summary

Shows:

- Total published videos
- Last successful data update
- Primary question

No portfolio-wide totals belong here.

### 3. Search, Filter, and Sort

Initial controls:

- Search by video title
- Filter by attention state
- Sort by priority
- Optional column visibility control

Planned v0.1 attention filters:

- Needs attention
- Strong performers
- Recent uploads
- Stable
- All videos

Planned sort options:

- Priority
- Upload date
- Views
- Watch time
- CTR
- Average view duration
- Comments
- Revenue, when available

A metric may appear as a sort option only when the channel authorization and selected period provide that metric.

### 4. Priority Video Rows

The default one-screen view shows up to five priority videos.

Each row includes:

- Thumbnail
- Title
- Age or publication date
- Views
- CTR, when available
- Average view duration
- Watch time
- Plain-language attention reason
- Direct action to open the Video Workspace

Rows may display one supporting comparison sentence. They must not display multiple competing explanations.

### 5. Attention Reasons

Initial deterministic reasons may include:

- Fast start
- Low CTR
- Strong watch time
- High conversation
- Declining velocity
- Renewed interest
- Stable
- Insufficient data

Each reason must have a calculation path. Labels are summaries, not subjective grades.

## Fair Comparison Rules

### Recent Videos

A recent upload should be compared with:

1. The creator's previous N uploads at the same age, when sufficient data exists; or
2. An age-adjusted channel baseline for comparable uploads.

The interface must name which comparison was used.

### Older Videos

Older videos may be compared using the selected date range, lifetime performance, or a clearly named rolling baseline.

### Mixed Formats

Shorts, livestreams, and standard videos must not be blended into one baseline when their metrics are not comparable. Format filters or separate baselines are required before implementation.

## Interactions

### Select Video Row

Opens the Video Workspace for that video.

### Search

Filters the current video index by title. Search should not trigger a remote YouTube query after the local index exists.

### Filter

Updates the visible rows and summary count without losing the selected date range.

### Sort

Reorders the current result set. The selected sort and direction must be visible.

### View All Videos

Opens the complete paginated or virtualized video directory. It is a separate state from the five-row priority overview and may use internal scrolling within the data region.

### Column Selector

Allows hiding optional columns on desktop. Required identity and attention columns cannot be removed.

## Empty and Special States

### No Published Videos

Show:

> No published videos were found for this channel.

For a pre-launch channel, link back to the Channel Dashboard. Do not fabricate performance recommendations.

### Insufficient Historical Data

Show recent videos with available raw metrics and label comparisons as:

> Not enough history for a reliable baseline yet.

### Missing Analytics Permission

Display public metrics that are available. Private metrics such as CTR, watch time, retention, or revenue must show `Unavailable` with a permission explanation.

### Partial API Failure

Render cached or successfully retrieved video rows. Mark affected metrics as stale or unavailable and show a compact warning.

### Revoked Authorization

Show the locally stored index in read-only cached mode when safe, clearly label its age, and provide a reconnect path.

### Deleted or Private Videos

Preserve historical records when previously collected. Clearly label current visibility state and never imply that YT-Companion changed it.

### Loading

Use stable row skeletons matching the final table geometry. Do not animate counters or rearrange the layout after each metric arrives.

### Total Failure

Show:

- What failed
- Last successful update time, if known
- Retry action
- Link to connection health

Do not display empty zeros.

## Responsive Behavior

### Tablet

- Keep thumbnail, title, views, and attention reason visible.
- Move secondary metrics into a compact expandable details row.
- Keep search, filter, and sort accessible without horizontal page scrolling.

### Mobile

The mobile view becomes a compact list rather than a squeezed table.

Each item shows:

- Thumbnail
- Title
- Age
- Primary metric
- Attention reason
- Expand control for secondary metrics
- Open Workspace action

Mobile pages may scroll vertically because the desktop one-screen rule is not physically meaningful on small screens. Initial content should still prioritize the highest-value items first.

## Accessibility

- Table headers must be programmatically associated with their columns.
- Sort state must be announced and not communicated by icon direction alone.
- Trend and attention states must include text labels.
- Thumbnails require useful alt text or may be marked decorative when the title already identifies the video.
- Entire rows may be clickable only if keyboard users receive an equivalent focusable action.
- Focus order must follow the visible reading order.
- Data changes caused by filters should be announced politely to assistive technology.

## Performance Expectations

- The priority view should render from locally stored data without requiring every video to be fetched from YouTube during page load.
- Initial LAN target: useful content visible within 2 seconds under normal reference conditions.
- Sorting and filtering the local index should feel immediate.
- Large video libraries must use pagination or virtualization in the full directory.
- Thumbnail loading must not block text and metric rendering.

## Acceptance Criteria

Feature 006 is valid when:

- The primary question is explicit.
- The initial desktop priority view fits at 1920×1080 without page-level vertical scrolling.
- Up to five videos can be compared without visual clutter.
- Default ordering is based on documented attention priority, not an unexplained score.
- Recent-video comparisons are age-matched or explicitly contextualized.
- Every attention reason has an evidence path.
- Missing metrics are labeled unavailable rather than zero.
- A video opens its workspace in one clear action.
- Empty, loading, partial-failure, revoked-authorization, deleted-video, tablet, and mobile states are defined.
- No control or visual element exists only because it looks impressive.

## Out of Scope

- Editing video metadata
- Uploading or scheduling videos
- Changing privacy state
- Bulk YouTube actions
- AI-generated quality scores
- Automatic deletion
- CSV export in v0.1
- Cross-channel video blending
- Video Workspace design, which is a separate feature
