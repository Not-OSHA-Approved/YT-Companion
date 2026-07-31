# YT-Companion

A self-hosted analytics and insight platform for YouTube creators.

YT-Companion is designed to complement YouTube Studio with long-term historical tracking, creator-focused observations, title and thumbnail analysis, and evidence-based AI insights.

> **Project status:** Foundation stage. No functional release is available yet.

## Core Principles

- Self-hosted first
- Read-only by default
- Never modify a YouTube channel without explicit authorization
- Historical analytics are first-class data
- Every feature must answer a question creators actually ask
- AI insights must be traceable to collected data
- Multiple users and multiple channels must remain isolated and independently authorized

## Planned v0.1 Scope

YT-Companion v0.1 will:

- Authenticate users through Google OAuth
- Connect one or more authorized YouTube channels
- Read channel and uploaded-video information
- Read subscriber count, views, watch hours, and available revenue data
- Store daily snapshots in SQLite
- Display a responsive dark-mode dashboard
- Provide read-only Creator Insights backed by collected data

YT-Companion v0.1 will not edit videos, upload content, change thumbnails, schedule content, or write to YouTube.

## Multi-User Model

YT-Companion is being designed for shared installations. An installation may have multiple application users, and each user may be granted access to one or more creator profiles. Google authorization and channel permissions will be stored separately from application identity.

This allows, for example, two household members to use the same installation without sharing a login or mixing channel permissions.

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for the initial identity and tenancy model.

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

The project is in its initial foundation stage. Development practices are documented in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

YT-Companion is licensed under the MIT License. See [LICENSE](LICENSE).
