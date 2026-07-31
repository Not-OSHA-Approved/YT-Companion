# Development Log

## 2026-07-31 — Feature 001: Repository Foundation

### Design

Established a public, Docker-first, read-only project foundation with professional repository structure, safety rules, and a strict one-feature-at-a-time workflow.

### Implementation

Added the README, MIT license, contribution policy, security policy, ignore rules, architecture document, project status, and development log.

### Test

Repository files were fetched from the default branch after creation to confirm accessibility and content persistence.

### Validation

Validated that the repository is public, uses `main` as its default branch, and that the connected GitHub integration has administrative and push access. Confirmed that the documented v0.1 boundary contains no YouTube write capability.

### Documentation

Created the initial project documentation set.

### Result

Feature 001 completed. No application code was introduced.

## 2026-07-31 — Feature 002: Creator Portfolio Product Model

### Design

Corrected the initial assumption that a shared household installation required separate YT-Companion user accounts. Defined one trusted installation containing one creator portfolio and multiple independently authorized YouTube channels.

Established the creator cockpit direction: readable plain-language summaries first, with detailed evidence and analytics available underneath.

### Implementation

Updated the README and architecture documentation. Added the product vision document covering the portfolio overview, channel switcher, dashboard hierarchy, Producer insights, video workspaces, Title Lab, and Thumbnail Lab.

### Test

Fetched the updated files from the default branch and verified that the obsolete mandatory household-account requirement was removed.

### Validation

Confirmed that channel histories remain isolated, Google authorizations remain independent, and future multi-user support is not prevented even though it is deferred.

### Documentation

Updated project status and documented the progressive-disclosure interface requirement.

### Result

Feature 002 completed. No application code was introduced.

## 2026-07-31 — Feature 003: Deployment and Access Model

### Design

Selected `https://companion.farwellonline.com` as the planned address for the reference installation.

Separated three responsibilities:

- Cloudflare Access controls who may open the externally reachable dashboard.
- Google OAuth grants read-only access to connected YouTube channels.
- YT-Companion provides one shared creator portfolio without duplicating household authentication in v0.1.

### Implementation

Added `docs/DEPLOYMENT-ACCESS.md` and updated the architecture document. The reference deployment uses Docker on Proxmox behind Cloudflare Tunnel, with no inbound router port forwarding.

### Test

Reviewed the documented request path and responsibility boundaries to confirm that external access does not depend on exposing the application container directly to the public internet.

### Validation

Confirmed that LAN-only deployment remains supported, the personal hostname is not an application constant, and Cloudflare protection does not replace secure OAuth handling or secret storage.

### Documentation

Documented the reference topology, configuration concepts, security requirements, and ownership boundaries.

### Result

Feature 003 completed. No application code or live Cloudflare configuration was introduced.

## 2026-07-31 — Feature 004: Portfolio Overview Wireframe

### Design

Defined the Portfolio Overview as the first YT-Companion screen and gave it one primary question:

> **Which channel deserves my attention today?**

Adopted the one-screen desktop rule, row-based channel presentation, prioritized channel ordering, concise Producer observations, and visible snapshot health.

### Explain

Rows were selected instead of cards because they provide better scanability, density, sorting potential, and support for portfolios larger than the reference household installation.

The initial desktop view shows up to six non-archived priority channels. Larger portfolios use a separate full channel directory rather than forcing the landing page to scroll.

### Implementation

Added:

- `docs/WIREFRAMES/01-Portfolio.md`
- `docs/WIREFRAMES/01-Portfolio.svg`

The specification defines desktop and mobile behavior, summary metrics, channel states, interactions, loading and error states, accessibility expectations, performance targets, scaling rules, and acceptance criteria.

### Test

Reviewed the wireframe dimensions and information hierarchy against the documented 1920×1080 reference viewport and the 1366×768 minimum usable desktop target.

Verified that the specification handles zero channels, partial channel failures, total load failure, more than six channels, archived channels, stale cached data, and unavailable analytics without inventing status information.

### Fix

Removed the earlier assumption that every connected channel must remain visible simultaneously on the first screen. The corrected design keeps the six highest-priority channels visible and routes larger portfolios to a dedicated directory while preserving the no-page-scroll requirement.

### Regression Test

Confirmed that Feature 004 does not change the read-only v0.1 boundary, does not reintroduce household application accounts, and does not conflict with the Cloudflare access model.

### Validation

Confirmed that:

- The primary question is explicit.
- The initial desktop view avoids page-level vertical scrolling.
- Every visible section supports a creator decision.
- Producer observations require an evidence path.
- Channel status cannot be guessed when data is insufficient.
- No visual feature exists solely for decoration.

### Documentation

Updated project status and recorded the completed UX decisions, edge states, and validation results.

### Result

Feature 004 completed. No application code was introduced.

## 2026-07-31 — Feature 005: Channel Dashboard Wireframe

### Design

Defined the Channel Dashboard around one primary question:

> **What should I know about this channel today?**

The initial desktop view contains channel identity, six core metrics, one primary Producer observation, no more than two Top Movers, three recent uploads, compact historical direction, and collection health.

### Explain

The dashboard deliberately separates summary from analysis. It provides enough context to decide where to investigate while routing exact calculations, full charts, and detailed filters to evidence, Analytics, and future Video Workspace screens.

The default comparison period is 28 days, and every comparison-capable section must use the selected period consistently or disclose that it cannot.

### Implementation

Added:

- `docs/WIREFRAMES/02-Channel-Dashboard.md`
- `docs/WIREFRAMES/02-Channel-Dashboard.svg`

The specification defines metric contracts, date-range behavior, Producer evidence, Top Movers thresholds, recent uploads, compact trends, collection health, responsive behavior, accessibility, performance targets, data requirements, edge states, and acceptance criteria.

### Test

Reviewed the 1600×900 visual wireframe and the written specification against the 1920×1080 one-screen reference and 1366×768 minimum desktop target.

Verified that all core sections fit in the initial layout and that deeper data is reached through explicit navigation rather than page-level scrolling.

### Fix

Rejected several misleading fallback behaviors during design:

- Unavailable revenue is labeled rather than shown as zero.
- Missing historical baselines use `Collecting baseline` rather than unstable percentages.
- Revoked authorization preserves historical read-only access instead of blanking the dashboard.
- Pre-launch channels use a purpose-built state rather than empty metric cards.
- Dormancy is reported as a fact, not turned into unsupported publishing advice.

### Regression Test

Confirmed that Feature 005 preserves the creator portfolio model, Cloudflare access boundary, independent Google authorization model, one-screen desktop rule, evidence requirement, and strict read-only v0.1 boundary.

### Validation

Confirmed that:

- The primary question is explicit.
- Every metric names its comparison context.
- Exactly one primary Producer observation appears.
- Every insight and movement has an evidence path.
- Missing data is never estimated or silently replaced.
- Pre-launch, dormant, loading, partial-failure, total-failure, revoked-authorization, and insufficient-history states are defined.
- Mobile readability takes priority over forcing desktop density onto a narrow screen.
- No element exists solely for decoration.

### Documentation

Updated project status and recorded the completed Channel Dashboard UX contract and validation results.

### Result

Feature 005 completed. No application code was introduced.

## 2026-07-31 — Feature 006: Videos Screen Wireframe

### Design

Defined the Videos screen around one primary question:

> **Which videos deserve my attention right now?**

Selected compact rows, a five-video priority view, deterministic attention reasons, and direct navigation into the future Video Workspace.

### Explain

The screen defaults to attention priority rather than upload date because its purpose is to help the creator decide where to investigate. It explicitly rejects unexplained AI scores and requires recent videos to be compared at similar ages or against clearly named age-adjusted baselines.

Shorts, livestreams, and standard videos must not share a baseline when their metrics are not meaningfully comparable.

### Implementation

Added:

- `docs/WIREFRAMES/03-Videos.md`
- `docs/WIREFRAMES/03-Videos.svg`

The specification defines search, filters, sorting, optional columns, video-row content, attention reasons, fair comparison rules, full-directory behavior, responsive layouts, accessibility, performance expectations, failure states, and acceptance criteria.

### Test

Reviewed the visual wireframe and written specification against the 1920×1080 one-screen target and the 1366×768 minimum desktop target.

Verified that five priority rows, controls, supporting comparison text, and collection health fit without page-level desktop scrolling.

### Fix

Removed several misleading or unnecessary concepts during design:

- Rejected a composite AI score because it would hide the calculation and encourage false precision.
- Required missing analytics to display as unavailable rather than zero.
- Separated the five-row priority view from the full video directory so large libraries do not break the one-screen rule.
- Required age-matched comparisons for new uploads so a one-day-old video is not compared unfairly with lifetime totals.
- Deferred CSV export because it does not help answer the current screen's primary question in v0.1.

### Regression Test

Confirmed that Feature 006 preserves the creator portfolio model, read-only boundary, channel isolation, evidence requirement, one-screen desktop rule, and progressive-disclosure design.

### Validation

Confirmed that:

- The primary question is explicit.
- Up to five videos can be scanned without clutter.
- Every attention reason has an evidence path.
- Recent-video comparisons identify their baseline.
- Missing data is never guessed.
- No YouTube write action is present.
- Empty, loading, partial-failure, revoked-authorization, deleted-video, tablet, and mobile states are defined.
- Every visible element supports recognition, comparison, navigation, or data trust.

### Documentation

Updated project status and recorded the Videos screen UX contract, comparison rules, edge cases, and validation results.

### Result

Feature 006 completed. No application code was introduced.
