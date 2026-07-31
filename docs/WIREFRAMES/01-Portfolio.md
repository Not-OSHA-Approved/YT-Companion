# Portfolio Overview Wireframe

## Feature

Feature 004 — Portfolio Overview

## Purpose

The Portfolio Overview is the first screen shown after YT-Companion opens.

It answers one question:

> **Which channel deserves my attention today?**

The screen is not a miniature analytics dashboard. It is a compact decision surface that identifies channel health, recent activity, and the most important Producer observations across the portfolio.

## Design Rules

The screen must follow these rules:

1. **One-screen rule** — the complete initial desktop view must fit within a 1920×1080 display at 100% browser zoom without page-level vertical scrolling.
2. **Overview first; details on demand** — the screen presents priorities, not complete analytics.
3. **Polish, not fluff** — every visible element must help the creator decide where to look next.
4. **Rows over cards** — channels use compact rows because rows scan, sort, and scale better.
5. **Producer speaks human** — observations use plain language and avoid hype.
6. **Evidence remains available** — observations lead to supporting calculations when selected.
7. **One click has value** — selecting a channel opens that channel's dashboard directly.

## Desktop Reference Viewport

The reference desktop viewport is 1920×1080 at 100% browser zoom.

The content region must remain usable at 1366×768. At that size, secondary text may be shortened, but the primary question, priority channel rows, synchronization state, and channel navigation must remain visible without page-level vertical scrolling.

## Desktop Layout

```text
┌────────────────────────────────────────────────────────────────────────────────────────────┐
│ YT-Companion      Portfolio                                      Search      Sync ✓   ⚙     │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ CREATOR PORTFOLIO                         Which channel deserves your attention today?       │
│                                                                                            │
│ 6 channels      3 active      4,077 subscribers      2 uploads this week      Updated 8m ago│
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ PRIORITY  CHANNEL                         STATUS         SUBSCRIBERS   LAST UPLOAD   PRODUCER │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│    1      Growing Old w/o Growing Old     Healthy            3,640     Yesterday     Growth  │
│           +18 this week                                                 Open dashboard  ›    │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│    2      Not OSHA Approved!              Opportunity          230     3 weeks ago    Publish │
│           Fastest-growing small channel                                Open dashboard  ›    │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│    3      Don't Call It Glamping          Pre-launch             —     No uploads     Ready   │
│           Connected and ready for its first video                      Open dashboard  ›    │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│    4      No BS Batteries                 Stable                 94     2 months ago   Steady  │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│    5      MrFrickinfrack8                 Dormant               103     4 months ago   Quiet   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│    6      Gen Xed Out                     Dormant                10     5 months ago   Quiet   │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ PRODUCER NOTICED                                                                           │
│ Growing Old generated most portfolio growth this week. Not OSHA Approved has the strongest │
│ recent subscriber momentum among smaller channels.                         View evidence ›  │
├────────────────────────────────────────────────────────────────────────────────────────────┤
│ Snapshot healthy · Last collection 8 minutes ago · Next scheduled collection 11:00 PM       │
└────────────────────────────────────────────────────────────────────────────────────────────┘
```

The values above are illustrative mock data, not claims about any real channel.

## Information Hierarchy

### 1. Application Header

Contains only:

- YT-Companion identity
- Current section: Portfolio
- Channel search/filter control
- Current synchronization health
- Settings entry point

The header must not contain decorative controls, notifications without actionable meaning, or duplicate navigation.

### 2. Portfolio Summary

Displays no more than five values:

- Connected channels
- Active channels
- Total public subscribers across compatible channels
- Uploads during the current week
- Age of the latest successful snapshot

Revenue is excluded because combining revenue across differently authorized channels can be misleading and because the Portfolio screen's primary job is prioritization.

### 3. Channel Priority Rows

Rows are ordered by attention priority, not alphabetically.

Each row may display:

- Priority position
- Channel name
- One concise secondary fact
- Computed channel state
- Subscriber count when available
- Last upload age
- One short Producer cue
- Direct dashboard affordance

The entire row is clickable. Keyboard focus and activation must work without requiring the small arrow target.

### 4. Producer Noticed

Displays one portfolio-level observation, or two short related observations when both fit without wrapping beyond two lines.

The section must never contain generic encouragement, motivational filler, or unsupported advice.

Selecting **View evidence** opens the Producer evidence view for the observation.

### 5. Snapshot Health

The footer answers: **Did the system actually collect the data?**

It shows:

- Current collector health
- Time of the latest successful collection
- Next scheduled collection

Selecting it opens snapshot history and collection diagnostics.

## Channel States

The following states are permitted in v0.1:

- **Healthy** — recent activity and key trends remain within or above the channel's established normal range.
- **Opportunity** — available evidence suggests a specific creator action may be worthwhile.
- **Stable** — no meaningful positive or negative movement requires attention.
- **Dormant** — the channel has not published within its configured or inferred activity window.
- **Pre-launch** — the channel is connected but has no public uploads.
- **Archived** — hidden from the default portfolio without deleting its local history.
- **Data issue** — authorization, collection, or data completeness prevents a reliable state.

These labels are computed from documented rules. They are not decorative badges and are not manually editable in v0.1.

A status must not be shown when the required data is insufficient. Use **Data issue** or a neutral unavailable state rather than guessing.

## Priority Rules

Priority is based on actionable need, not simply on channel size.

The eventual deterministic priority calculation may consider:

- Collection or authorization failures
- Significant negative deviation from the channel's baseline
- Unusually strong positive momentum worth understanding
- Recent uploads requiring early-performance review
- Meaningful publishing gaps
- Pre-launch readiness

Exact formulas belong to a later data feature. This wireframe requires only that priority be explainable and traceable.

## Channel Count and Scaling

The desktop initial view shows up to six non-archived channel rows.

When more than six channels exist:

- The six highest-priority channels remain visible.
- A compact **View all channels** action replaces the lowest-value secondary content, not the primary summary.
- The page itself still does not scroll.
- The full channel directory opens as a separate focused view with sorting and filtering.

Archived channels are excluded by default and are available through the full channel directory.

## Search Behavior

In v0.1, search filters connected channels by channel name.

Search does not search videos, titles, descriptions, or Producer observations until those features exist.

Filtering happens within the fixed content area and must not introduce page-level scrolling.

## Interactions

### Select a Channel

Opens the selected channel dashboard directly.

No confirmation dialog, intermediate menu, or modal is used.

### Select a Producer Cue

Opens the supporting observation and evidence for that channel.

### Select Sync Health

Opens snapshot history and collection diagnostics.

### Select Settings

Opens connection and application settings.

### Select View All Channels

Opens the full channel directory when the portfolio contains more channels than the initial view can display.

## Loading State

The application shell, labels, and stable layout appear immediately.

Summary values and rows use fixed-size skeleton placeholders so the page does not jump as data loads.

Loading copy must not pretend that stale cached values are current. When cached data is intentionally shown, its age remains visible.

## Empty State

When no channels are connected, the screen shows:

- YT-Companion title
- A plain explanation that no YouTube channels are connected
- One primary action: **Connect a YouTube channel**
- A short read-only authorization explanation

The empty state must fit within the same one-screen desktop layout.

## Partial Data State

When some channels load and others fail:

- Healthy channel rows remain usable.
- Affected channels show **Data issue**.
- The summary identifies incomplete data rather than silently omitting it.
- A direct diagnostics action is available.

One failed authorization must not make the entire portfolio unusable.

## Error State

A total portfolio-load failure shows:

- What failed in plain language
- Whether cached data is available and how old it is
- A retry action
- A diagnostics action

Raw exception text, stack traces, OAuth tokens, and internal secrets must never appear in the user interface.

## Mobile Behavior

Mobile is a focused companion view, not a compressed desktop table.

The mobile initial view shows:

1. Synchronization health
2. The highest-priority channel
3. Up to two additional priority channels
4. One Producer observation
5. A **View all channels** action

Rows become stacked compact summaries. Detailed secondary metrics move behind the channel dashboard.

Mobile may scroll because the one-screen rule applies to the initial desktop creator cockpit. Mobile must still place the highest-priority answer within the first viewport.

## Accessibility

- All interactive rows must be keyboard reachable.
- Focus state must be clearly visible.
- Status must not rely on color alone.
- Icons must have accessible names or be hidden from assistive technology when redundant.
- Text contrast must meet WCAG AA.
- Touch targets must be at least 44×44 CSS pixels on touch layouts.
- Relative dates such as **Yesterday** must expose an exact timestamp to assistive technology or through a tooltip/detail view.

## Performance Target

With locally cached summary data, the usable Portfolio Overview should appear within two seconds on the reference LAN deployment.

A later implementation feature will define measurable frontend and API performance tests. This wireframe does not claim that target has yet been achieved.

## Out of Scope

The Portfolio Overview does not include:

- Historical charts
- Video lists
- Revenue details
- Thumbnail previews
- Title analysis
- AI chat
- Channel editing
- YouTube write actions
- Manually assigned health labels
- Decorative animations

## Acceptance Criteria

Feature 004 is accepted when:

- The screen has one documented primary question.
- The desktop initial view fits within 1920×1080 without page-level vertical scrolling.
- The layout remains usable at 1366×768 without page-level vertical scrolling.
- Channels use rows rather than large cards.
- Up to six priority channels can be displayed in the initial view.
- More than six channels are handled without breaking the one-screen rule.
- Selecting a channel opens its dashboard directly.
- Portfolio summary data is limited to decision-relevant values.
- Producer observations are concise and evidence-linked.
- Loading, empty, partial-data, and total-error states are defined.
- Snapshot health is visible without dominating the screen.
- Archived channels are hidden by default without deleting history.
- No visual element exists solely because it looks impressive.
- No YouTube write capability is introduced.

## Validation Checklist

- [x] Primary question is explicit.
- [x] One-screen desktop rule is documented.
- [x] Rows were selected over cards for density and scalability.
- [x] More-than-six-channel behavior is defined.
- [x] Producer evidence path is defined.
- [x] Snapshot-health path is defined.
- [x] Accessibility requirements are defined.
- [x] Error and incomplete-data behavior are defined.
- [x] v0.1 scope remains read-only.
- [x] Mock values are clearly identified as illustrative.
