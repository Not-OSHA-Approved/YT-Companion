# Initial Architecture

## Purpose

YT-Companion is a self-hosted, Docker-first creator cockpit for YouTube analytics. The initial release is read-only and stores historical data locally.

## Core Boundaries

The application is divided into modules for YouTube authorization, channel management, data collection, persistence, analytics, insights, API delivery, and the web dashboard.

No module may bypass the authorization or channel-data boundaries of another module.

## v0.1 Creator Portfolio Model

The system must not assume one installation equals one YouTube channel.

### Installation

A self-hosted YT-Companion instance. v0.1 is intended for a trusted household or individual creator environment and does not require separate application-user accounts.

### Creator Portfolio

The top-level workspace containing every channel connected to the installation. It provides cross-channel navigation and summary analytics without merging the underlying channel histories.

### Google Authorization

A read-only OAuth grant used to discover and collect data from one or more YouTube channels. Tokens belong to an authorization record and must be encrypted at rest.

### YouTube Channel

A separately tracked channel with its own metadata, videos, thumbnails, snapshots, analytics, and insights. A channel records which authorization permits collection.

### Channel Status

A local classification used to organize the portfolio. Planned values include Active, Pre-launch, Dormant, and Archived. This status does not modify YouTube.

## Data Isolation

Every channel-derived record must include its YouTube channel identifier. Portfolio calculations may aggregate compatible metrics, but channel-level history must never be blended or attributed to the wrong channel.

Revenue and other private analytics must only be displayed when the relevant OAuth authorization permits access.

## Interface Model

The primary interface consists of:

1. A portfolio overview
2. A persistent channel switcher
3. A channel-specific creator cockpit

The landing experience answers **What should I know today?** before presenting detailed tables.

Information is layered:

- Clear summaries and plain-language observations first
- Expandable evidence, calculations, sample sizes, and historical detail underneath
- Consistent labels and visual hierarchy
- Dark mode first and responsive layouts

The goal is usability for non-technical creators without oversimplifying analytics for advanced users.

## v0.1 Runtime Direction

- PowerShell 7+ service layer
- REST API
- SQLite persistence
- Responsive dark-mode frontend
- Docker and Docker Compose deployment
- Scheduled daily snapshot collector
- Google OAuth using least-privilege read-only scopes

ASP.NET Core may be introduced later only if the PowerShell service approach cannot meet maintainability, authentication, concurrency, or web-hosting requirements.

## Creator Insights

Creator Insights are derived observations, not free-form guesses. Each insight must store or return:

- The observation
- The comparison period
- The metric and calculation used
- Sample size
- Supporting channel or video identifiers
- Confidence or limitation notes when appropriate

An insight must not be generated when the available data is insufficient. Correlation must not be presented as causation.

## Deferred Multi-User Authentication

Separate YT-Companion user accounts, roles, and permissions are not part of v0.1. The data model should avoid preventing future multi-user support, but no role system will be built until a real use case requires it.

## Safety Boundary

v0.1 contains no YouTube write path. Uploading, editing metadata, changing thumbnails, scheduling, or any other channel mutation is out of scope.
