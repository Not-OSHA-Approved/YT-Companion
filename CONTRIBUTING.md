# Contributing to YT-Companion

YT-Companion is developed one feature at a time.

## Required Feature Cycle

Every feature must complete these steps in order:

1. Design
2. Explain
3. Implement
4. Test
5. Validate
6. Commit
7. Update documentation

Do not combine unrelated features in one pull request or commit.

## Development Standards

- Target PowerShell 7 or newer.
- Use professional, descriptive names.
- Keep functions small, reusable, and independently testable.
- Keep YouTube access read-only unless a future feature explicitly documents and authorizes write access.
- Never log access tokens, refresh tokens, OAuth secrets, or sensitive revenue data.
- Treat users, creator profiles, channels, and Google authorizations as separate entities.
- Add or update Pester tests for behavior changes.
- Update project status and development log documentation.

## Branches and Commits

Use a dedicated branch for each feature. Prefer focused commit messages that describe the completed change.

## Pull Requests

A pull request should state:

- The creator question the feature answers
- The design decision
- What changed
- How it was tested
- How it was validated
- Documentation updated
- Known limitations

## AI Contributions

AI-generated code is welcome but must be reviewed, tested, and understood before merge. AI-generated insights in the application must always be traceable to stored data and must never invent statistics.
