# Amplyx Public Feedback Portal

This repository is the public feedback intake portal for Amplyx.

- Submit bugs, feature requests, compatibility reports, and general feedback here.
- Maintainers triage and implement work in the private source repository.
- Public issues are mirrored into private maintainer workflows using safe automation.

## What Is Public vs Private

- Public here: your submitted issue, discussion, and status updates.
- Private elsewhere: implementation details, internal triage notes, and sensitive context.

## How To Report Effectively

Include:

- Browser version
- Extension version
- Site/app URL or hostname
- Reproduction steps
- Expected vs actual behavior
- Screenshots and logs when available

## Contact

- `contact@riteshrana.engineer`

## Maintainer Setup

For cross-repository sync to work, configure this repository secret:

- `PRIVATE_REPO_SYNC_TOKEN`: fine-grained PAT with permission to dispatch events to `ambicuity/Amplyx---Volume-Booster-Audio-Controller`.

In the private source repository, also configure:

- `PUBLIC_REPO_SYNC_TOKEN`: fine-grained PAT with permission to dispatch back to this feedback repository.
