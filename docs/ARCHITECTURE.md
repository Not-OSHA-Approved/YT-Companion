# Initial Architecture

## Purpose

YT-Companion is a self-hosted, Docker-first analytics companion for YouTube creators. The initial release is read-only and stores historical data locally.

## Core Boundaries

The application is divided into modules for identity, YouTube authorization, data collection, persistence, analytics, insights, API delivery, and the web dashboard.

No module may bypass the authorization or data-access boundaries of another module.

## Multi-User and Multi-Channel Model

The system must not assume one installation, one user, or one channel.

### Application User

A person who can sign in to YT-Companion. Chris and Becky must have separate application-user records and sessions.

### Creator Profile

A workspace representing a creator, brand, household project, or channel-management context. A creator profile owns local analytics history and configuration.

### Creator Membership

Links an application user to a creator profile with a role. Initial planned roles are Owner and Viewer. Roles will be implemented only when their feature is designed.

### Google Authorization

Represents a user's OAuth grant. Tokens belong to an authorization record, not directly to the global installation. Authorization records must be encrypted at rest.

### YouTube Channel

Represents a channel returned by an authorized Google account. A creator profile may connect to one or more channels, and a channel connection must record which authorization permits collection.

This separation supports shared household access without requiring shared passwords and supports future installations serving multiple creators.

## Data Isolation

Every channel-derived record must be associated with a creator profile and channel identifier. Queries must enforce creator-profile membership before returning private analytics or revenue data.

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

An insight must not be generated when the available data is insufficient.

## Safety Boundary

v0.1 contains no YouTube write path. Uploading, editing metadata, changing thumbnails, scheduling, or any other channel mutation is out of scope.
