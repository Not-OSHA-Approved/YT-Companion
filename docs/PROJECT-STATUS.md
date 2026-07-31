# Project Status

## Current Version

Pre-release product-definition stage.

## Active Feature

None. Feature 006 — Videos Screen Wireframe is complete.

## Status

Repository foundation, creator portfolio model, deployment access model, and the first three primary UX screens are validated.

## Completed

- Public GitHub repository created
- Project mission and safety principles documented
- MIT license added
- Contribution and security policies added
- Secret, token, database, and runtime-data ignore rules added
- Development workflow established
- Creator portfolio and multi-channel model documented
- Unnecessary v0.1 household user accounts removed from scope
- Creator cockpit interface direction documented
- Progressive disclosure requirement documented: approachable summaries with expandable technical detail
- Creator Insights evidence requirements documented
- Reference deployment address selected: `companion.farwellonline.com`
- Cloudflare Tunnel and Cloudflare Access responsibilities documented
- Google OAuth separated from dashboard-access control
- LAN-only deployment retained as a supported option
- Portfolio Overview primary question and one-screen desktop rule documented
- Row-based priority layout selected for channel scalability
- Channel Dashboard metrics, Producer summary, recent uploads, trends, and failure states documented
- Videos screen priority model, fair-comparison rules, filters, sorting, responsive states, and failure handling documented
- Grayscale visual wireframes added for Portfolio, Channel Dashboard, and Videos

## Product Model

v0.1 targets one trusted self-hosted installation containing one creator portfolio and multiple independently authorized YouTube channels.

Separate application user accounts, roles, and permissions are deferred until a real use case requires them.

## Reference Deployment

The reference installation will run under Docker on Proxmox and be published through Cloudflare Tunnel at `https://companion.farwellonline.com`.

Cloudflare Access protects the externally reachable dashboard. Google OAuth is used only to authorize read-only YouTube data collection.

No live Cloudflare resources or application containers have been created yet.

## Interface Direction

### Portfolio Overview

Answers:

> **Which channel deserves my attention today?**

Its initial desktop view fits without page-level vertical scrolling and displays up to six prioritized non-archived channels.

### Channel Dashboard

Answers:

> **What should I know about this channel today?**

It combines core metrics, one primary Producer observation, Top Movers, recent uploads, compact trends, and data-health context.

### Videos

Answers:

> **Which videos deserve my attention right now?**

Its default view shows up to five priority videos with age-matched or explicitly contextualized comparisons. It does not use unexplained AI scores or compare unlike formats through a shared baseline.

## Next Feature

Feature 007 will be selected before further design or application implementation begins. No Feature 007 work has begun.

## v0.1 Boundary

v0.1 remains strictly read-only. No upload, edit, thumbnail-change, scheduling, privacy-state change, or other YouTube mutation capability is permitted.
