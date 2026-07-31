# Project Status

## Current Version

Pre-release product-definition stage.

## Active Feature

None. Feature 003 — Deployment and Access Model is complete.

## Status

Repository foundation, creator portfolio model, and deployment access model validated.

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

## Product Model

v0.1 targets one trusted self-hosted installation containing one creator portfolio and multiple independently authorized YouTube channels.

Separate application user accounts, roles, and permissions are deferred until a real use case requires them.

## Reference Deployment

The reference installation will run under Docker on Proxmox and be published through Cloudflare Tunnel at `https://companion.farwellonline.com`.

Cloudflare Access protects the externally reachable dashboard. Google OAuth is used only to authorize read-only YouTube data collection.

No live Cloudflare resources or application containers have been created yet.

## Next Feature

Feature 004 will be selected before application implementation begins. No Feature 004 work has begun.

## v0.1 Boundary

v0.1 remains strictly read-only. No upload, edit, thumbnail-change, scheduling, or other YouTube mutation capability is permitted.
