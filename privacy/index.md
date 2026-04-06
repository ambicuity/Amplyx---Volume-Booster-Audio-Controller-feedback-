# Amplyx Privacy Policy

Last updated: April 6, 2026

Amplyx is a Chrome extension for tab audio control, equalizer tuning, and optional local smart profile suggestions. This policy explains what data Amplyx processes, where it is stored, and how you control it.

## Scope

This policy applies to Amplyx extension surfaces:

- Popup (`popup.html`)
- Side panel (`sidepanel.html`)
- Workspace (`workspace.html`)
- Settings (`settings.html`)
- Background service worker and offscreen audio runtime

## Data Amplyx Processes

Amplyx processes only data required for extension behavior.

1. Tab context metadata
- Active tab URL
- Active tab title
- Hostname
- Tab identifier and window identifier

2. Audio control state
- Volume level, max volume, selected preset, and filter values
- Per-tab runtime state for active sessions
- Optional per-site remembered audio profile state

3. User settings
- Theme and UI preferences
- Audio preferences (default preset, step size, max boost)
- AI/safety preferences (`recommendationsEnabled`, `safeListeningEnabled`, `safetyMaxVolume`, `cloudOptIn`)

4. Runtime diagnostics (session-only)
- Non-fatal runtime/offscreen telemetry events used for reliability debugging
- Stored in volatile session storage and cleared when extension runtime resets

## How Amplyx Uses This Data

Amplyx uses processed data only to provide requested functionality:

- Initialize and control tab-local audio processing
- Persist user preferences
- Restore remembered audio state (when enabled)
- Provide safe-listening guardrails
- Provide local smart profile recommendations and capability status

## Storage and Retention

Amplyx uses browser-managed extension storage:

- `chrome.storage.session`
  - `tabAudioState`
  - `runtimeTelemetry`
- `chrome.storage.local`
  - `userSettings`
  - `siteAudioState`

Retention behavior:

- Session data is cleared when extension runtime reloads/restarts.
- Persistent settings and site profiles remain until changed by user or extension removal.

## AI and Model Processing

Amplyx is designed for offline-first AI behavior:

- Smart recommendation logic works with deterministic local fallback heuristics even when built-in AI APIs are unavailable.
- When built-in browser AI APIs are available and enabled, capability checks and local processing occur in-browser.
- Amplyx does not require cloud AI for core operation.
- Optional cloud AI fallback is user-controlled (`cloudOptIn`) and disabled by default.

## Data Sharing and Third Parties

Amplyx does not sell personal information.

Amplyx does not intentionally transmit tab audio data or page content to developer-operated servers for core features.

Amplyx may open third-party destinations only from explicit user actions (for example support links). Once opened, those destinations are governed by their own privacy policies.

## Permissions and Purpose

- `activeTab`: operate on user-selected active tab context
- `tabs`: read active tab metadata and open extension pages
- `storage`: persist settings and local state
- `sidePanel`: provide side panel control surface
- `tabCapture`: obtain media stream id for tab audio processing
- `offscreen`: host offscreen audio graph runtime

Amplyx does not request persistent `<all_urls>` host permissions in the current audio-first architecture.

## Security Approach

- Manifest V3 service worker architecture
- Extension page CSP with `script-src 'self'`
- Runtime message schema validation and strict message-type allowlists
- Offscreen message boundary allowlist

## Your Controls

You can:

- Change or reset settings in `settings.html`
- Disable remembered per-site audio state
- Disable smart recommendations
- Enable/disable safe listening guardrails
- Remove the extension at any time

## Policy Changes

If this behavior changes materially, this document and date will be updated.

## Contact

For privacy or security questions:

- contact@riteshrana.engineer
