# Security Policy

YT-Companion handles OAuth credentials, channel analytics, and potentially sensitive revenue data.

## Supported Versions

No production release is currently available. Security support begins with the first published version.

## Reporting a Vulnerability

Do not open a public issue containing secrets, tokens, private analytics, or exploit details. Use GitHub's private vulnerability reporting feature when available.

Include:

- A description of the issue
- Reproduction steps
- Affected version or commit
- Potential impact
- Any suggested mitigation

## Security Principles

- Read-only YouTube scopes by default
- Least-privilege authorization
- Separate application identity from Google authorization
- Encrypt refresh tokens and secrets at rest
- Never expose one creator profile's data to another without explicit membership
- Never place secrets in logs, exceptions, exports, or telemetry
- Require explicit authorization for any future write-capable feature
