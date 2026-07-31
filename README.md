# YT-Companion

A self-hosted creator cockpit for YouTube analytics, historical tracking, and evidence-based insights.

YT-Companion complements YouTube Studio. It is designed to answer: **What should I know today?**

> **YT-Companion is not a clone of YouTube Studio.**
>
> It is a creator cockpit designed to help you understand your channels, preserve their history, and make better publishing decisions.

> **Project status:** Foundation and product-model stage. No functional release is available yet.

## Core Principles

- Self-hosted first
- Read-only by default
- Never modify a YouTube channel without explicit authorization
- Historical analytics are first-class data
- Every feature must answer a question creators actually ask
- AI insights must be traceable to collected data
- Multiple channels must remain independently authorized and analytically isolated
- The interface must be approachable without hiding meaningful detail
- Polish, not fluff: every screen element must serve a creator-facing purpose
- Overview first; details on demand

## Creator Portfolio

A YT-Companion installation contains a creator portfolio with one or more connected YouTube channels. The user can switch between an individual channel dashboard and a portfolio overview.

v0.1 does not require separate household user accounts, roles, or permissions. Authentication for remote or multi-user installations may be added later as a separate feature.

Each connected channel retains its own:

- Google OAuth authorization
- Analytics history
- videos and thumbnails
- Creator Insights
- channel status, such as active, pre-launch, dormant, or archived

## Dashboard Direction

The landing page should not be a wall of numbers. It should lead with:

- Today at a Glance
- Creator Insights
- Top Movers
- Recent Uploads
- Historical Trends

Detailed analytics remain available through progressive disclosure so casual users can understand the dashboard quickly while advanced users can inspect calculations, comparisons, and source data.

## Planned v0.1 Scope

YT-Companion v0.1 will:

- Authorize one or more YouTube channels through Google OAuth
- Read channel and uploaded-video information
- Read subscriber count, views, watch hours, and available revenue data
- Store daily snapshots in SQLite
- Display a responsive dark-mode dashboard
- Provide a portfolio overview and channel switcher
- Provide read-only Creator Insights backed by collected data

YT-Companion v0.1 will not edit videos, upload content, change thumbnails, schedule content, or write to YouTube.

## Technology Direction

- PowerShell 7+
- REST API
- SQLite for v0.1
- PostgreSQL support later
- Responsive dark-mode web frontend
- Docker and Docker Compose
- Google OAuth
- YouTube Data API v3
- YouTube Analytics API
- Pluggable AI providers, including local models

## Development Workflow

Every feature follows this sequence:

1. Design
2. Explain
3. Implement
4. Test
5. Validate
6. Commit
7. Update documentation

Only one feature is developed at a time.

## Repository Layout

```text
src/            Application source code
tests/          Automated tests
docs/           Architecture, decisions, roadmap, and project records
docker/         Container-related files
scripts/        Development and maintenance scripts
.github/        GitHub templates and automation
```

## Security

Do not commit OAuth client secrets, access tokens, refresh tokens, channel credentials, database files, or local configuration containing secrets.

Security concerns should be reported according to [SECURITY.md](SECURITY.md).

## Contributing

Development practices are documented in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

YT-Companion is licensed under the MIT License. See [LICENSE](LICENSE).
