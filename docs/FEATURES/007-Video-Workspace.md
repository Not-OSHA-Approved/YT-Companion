# Feature 007 — Video Workspace Wireframe

## Design

Defined the Video Workspace as a case file for one video, answering:

> **Why is this video performing the way it is?**

The screen combines current video identity, age-appropriate performance context, one primary Producer finding, a timeline preview, an evidence snapshot, metadata-history paths, creator notes, and collection health.

## Explain

The workspace is intentionally not a clone of YouTube Studio. Its purpose is to preserve and explain the video's history.

The Evidence Engine owns deterministic calculations. Producer may translate an approved finding into readable language, but swapping or disabling an LLM cannot change the underlying evidence.

Title, thumbnail, traffic, and performance changes may be correlated in time, but proximity alone is never sufficient to claim causation.

## Implementation

Added:

- `docs/WIREFRAMES/04-Video-Workspace.md`
- `docs/WIREFRAMES/04-Video-Workspace.svg`

Updated `docs/PROJECT-STATUS.md`.

## Test

Reviewed the 1600×900 visual wireframe and written specification against the 1920×1080 reference viewport and 1366×768 minimum desktop target.

Confirmed that the initial case-file view contains identity, seven performance metrics, one finding, case summary, five-event timeline preview, evidence snapshot, tabs, and collection health without page-level desktop scrolling.

## Fix

The design rejects several misleading behaviors:

- Metadata changes detected from snapshots cannot be shown with false exact timestamps.
- Missing CTR or retention cannot be inferred from other metrics.
- Newly published videos cannot receive strong findings from tiny samples.
- Title or thumbnail changes cannot be labeled causal merely because performance changed afterward.
- Deleted, private, or authorization-disconnected videos retain their local historical case files.

## Regression Test

Confirmed that Feature 007 preserves:

- The one-screen desktop rule
- Read-only YouTube behavior
- Independent channel and video history
- Evidence-linked Producer findings
- Fair age-matched comparisons
- Progressive disclosure
- Cloudflare and Google OAuth responsibility boundaries

## Validation

Confirmed that:

- The primary question is explicit.
- Every finding exposes comparison group, sample size, metrics, calculation context, confidence, limitations, and supporting identifiers.
- Exact, snapshot-derived, and manual timestamps are distinguished.
- Local creator notes are clearly separated from YouTube data.
- Historical titles and thumbnails are preserved without providing edit actions.
- New, insufficient-history, deleted/private, revoked-authorization, partial-failure, tablet, and mobile states are defined.
- No element exists solely for decoration.

## Result

Feature 007 completed. No application code was introduced.
