# Project Status

## Current Version

Pre-release product-definition stage.

## Active Feature

None. Feature 005 — Channel Dashboard Wireframe is complete.

## Status

Repository foundation, creator portfolio model, deployment access model, Portfolio Overview, and Channel Dashboard UX specifications are validated.

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
- Progressive disclosure requirement documented
- Creator Insights evidence requirements documented
- Reference deployment address selected: `companion.farwellonline.com`
- Cloudflare Tunnel and Cloudflare Access responsibilities documented
- Google OAuth separated from dashboard-access control
- LAN-only deployment retained as a supported option
- Portfolio Overview primary question and one-screen desktop rule documented
- Row-based priority layout selected for channel scalability
- Portfolio loading, empty, partial-data, error, mobile, accessibility, and performance expectations defined
- Grayscale Portfolio Overview wireframe added
- Channel Dashboard primary question and information hierarchy documented
- Today at a Glance metric contract and comparison labeling defined
- Producer, Top Movers, Recent Uploads, compact trends, and collection-health behavior defined
- Pre-launch, dormant, loading, partial-failure, total-failure, revoked-authorization, and insufficient-history states defined
- Grayscale Channel Dashboard wireframe added

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

Its initial desktop view fits without page-level vertical scrolling and displays prioritized channels, one evidence-linked Producer observation, and collection health.

### Channel Dashboard

Answers:

> **What should I know about this channel today?**

Its initial desktop view fits without page-level vertical scrolling and presents channel identity, six core metrics, one primary Producer observation, no more than two Top Movers, three recent uploads, compact historical direction, and collection health.

Every metric comparison names its period. Missing permission or unavailable data is labeled and is never replaced with zero or an estimate.

## Next Feature

Feature 006 will be selected before application implementation begins. No Feature 006 work has begun.

## v0.1 Boundary

v0.1 remains strictly read-only. No upload, edit, thumbnail-change, scheduling, or other YouTube mutation capability is permitted.
