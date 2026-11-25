# Specification: `github-sync`

## Purpose
Define how the workspace, browser recording, OpenSpec artifacts, and conversation export are published to GitHub.

## Requirements

### Requirement: Repository Creation & Push
The system SHALL create an empty GitHub repository via the authenticated Chrome session and push all workspace artifacts via local Git CLI.

#### Scenario: Create `DIC4` and Push `main`
- **GIVEN** the user is logged into GitHub in Chrome
- **WHEN** the `browser` subagent creates an empty repository named `DIC4` at `https://github.com/new`
- **THEN** local Git CLI SHALL initialize `main`, commit all workspace files (including `overleaf_upload_recording.mp4`, `README.md`, `conversation_export.md`, and `openspec/`), and push to `origin main`.
