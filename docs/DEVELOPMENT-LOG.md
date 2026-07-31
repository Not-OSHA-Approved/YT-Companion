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
