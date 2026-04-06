# Maintainer Setup

This document is for maintainers configuring public/private issue synchronization.

## Required repository secrets

In `ambicuity/Amplyx---Volume-Booster-Audio-Controller-feedback-`:

- `PRIVATE_REPO_SYNC_TOKEN`

In `ambicuity/Amplyx---Volume-Booster-Audio-Controller`:

- `PUBLIC_REPO_SYNC_TOKEN`

Use fine-grained PATs with least privilege required for issue and repository dispatch operations.

## Workflow overview

- `public-feedback-intake.yml`
  - Trigger: public issue opened/edited/reopened
  - Creates or updates sync labels and tracking comment
  - Dispatches issue payload to private repository

- `private-feedback-sync.yml` (private repo)
  - Trigger: repository dispatch + private issue lifecycle updates
  - Creates/updates mirrored private issue
  - Dispatches close/reopen state back to public repository

- `public-close-from-private.yml`
  - Trigger: repository dispatch from private repo
  - Closes/reopens public issue and updates status comment/labels

## Operational notes

- Keep sync markers in issue comments unchanged to preserve idempotent updates.
- Validate secrets after rotation by opening a test public issue.
- If dispatch fails, inspect failed workflow logs first (`gh run view <id> --log-failed`).
