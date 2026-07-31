# Deployment and Access Model

## Purpose

YT-Companion is designed to run as a self-hosted application while remaining securely accessible from ordinary web browsers.

The planned production address for the reference installation is:

`https://companion.farwellonline.com`

This address is installation-specific and is not hard-coded into the application.

## Reference Deployment

```text
Browser
   |
   v
Cloudflare DNS and HTTPS
   |
   v
Cloudflare Access
   |
   v
Cloudflare Tunnel
   |
   v
YT-Companion on Docker / Proxmox
```

The application remains hosted on the owner's infrastructure. Cloudflare provides the public hostname, encrypted transport, and protected route to the local service.

## Access Responsibilities

### Cloudflare Access

Controls who may open the YT-Companion web interface from outside the trusted network.

For the reference household installation, Cloudflare Access may allow approved email addresses or one-time passcode authentication.

Cloudflare Access is not the YouTube authorization system.

### Google OAuth

Authorizes YT-Companion to read data from connected YouTube channels.

Each Google authorization must use the minimum required read-only scopes. OAuth tokens must be encrypted at rest and must never be placed in source control.

Google OAuth does not determine who may open the YT-Companion dashboard.

### YT-Companion

Provides the shared creator portfolio, channel switcher, analytics, historical snapshots, and Producer insights.

Separate YT-Companion household accounts are not required for v0.1. The reference installation is a trusted shared creator cockpit protected at the network edge.

## Network Requirements

The reference deployment should require:

- No inbound router port forwarding
- No direct exposure of the application container to the public internet
- HTTPS for remote access
- A persistent Cloudflare Tunnel connector
- Local persistent storage for the database, configuration, thumbnail archive, and backups

The application should still support LAN-only deployment for users who do not want remote access or Cloudflare.

## Configuration

The external hostname must be configurable through environment variables or deployment configuration. Example values may use `companion.example.com`; personal domain names must not be embedded in reusable application defaults.

Expected configuration concepts include:

- Public application URL
- Internal listening address and port
- OAuth callback URL
- Trusted proxy headers
- Secure-cookie behavior
- Cloudflare Access integration status

The exact variable names will be defined only when the deployment feature is implemented.

## Security Notes

Cloudflare protection does not remove the need for secure application design.

YT-Companion must still:

- Validate OAuth state and callback data
- Encrypt stored refresh tokens
- Avoid logging secrets
- Use secure cookies when served over HTTPS
- Respect forwarded-protocol headers only from configured trusted proxies
- Provide backup and recovery guidance

## v0.1 Decision

For the reference installation:

- Host YT-Companion on Docker under Proxmox
- Publish it at `companion.farwellonline.com`
- Route traffic through Cloudflare Tunnel
- Use Cloudflare Access as the external front door
- Use Google OAuth solely for read-only YouTube authorization
- Keep the application itself as one shared creator portfolio
