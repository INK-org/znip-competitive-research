# Znip Priority Roadmap

## Phase 0 — Capture spine (P0)

Ship a native-feeling menu-bar app with:

1. Permissions onboarding: Screen Recording, Microphone, Camera, Accessibility only when needed.
2. Area/window/display/fullscreen capture.
3. Global shortcuts with conflict detection.
4. Quick Access Tray with save, copy, reveal, edit, drag and delete.
5. Local history and unified library.
6. Crop + core annotation tools.
7. Secure blur/pixelate.
8. Basic recording with system/mic audio.
9. MP4/GIF export.
10. Offline-first state and crash-safe recovery.

**Demo bar:** take a screenshot, annotate it, copy it, drag it into another app, record a 30-second clip, export it, find both items in history — all without signing in.

## Phase 1 — Differentiation (P1)

1. Scrolling capture vertical/horizontal.
2. Crosshair/magnifier/freeze.
3. Background tool with auto-balance and presets.
4. Editable project files.
5. Webcam bubble, click highlights, keystrokes.
6. Studio editor with trim, zoom keyframes, cursor smoothing and motion blur.
7. Full-page web capture with viewport/breakpoint/light-dark modes.
8. On-device OCR.
9. Local AI naming, tags and summaries on Apple silicon.
10. Search across filename, OCR, tags, summaries and transcripts.
11. Optional one-click share links.

**Demo bar:** turn a raw recording into a polished vertical product walkthrough, then find it by a phrase visible inside the capture, all while offline until the user chooses Share.

## Phase 2 — Power-user moat (P2)

1. Social export presets.
2. Captions/transcription.
3. Saved searches and smart collections.
4. Floating references.
5. Hide desktop icons.
6. Capture reminders.
7. Batch operations.
8. Automation URL scheme.
9. Display/audio/device resilience hardening.
10. Import compatibility for common image/video formats and legacy projects.

## Phase 3 — Optional cloud/team layer (P3)

1. Hosted share pages.
2. Expiry/password/revoke/access control.
3. Searchable cloud library.
4. Comments/reactions.
5. Custom domains/branding.
6. Team seats, admin, SSO and SCIM.

Keep this phase modular. Znip's core value must not depend on a cloud account.

## Pricing thesis

Undercut observed competitors while avoiding a loss-leading cloud promise:

- **Free/local:** complete capture, annotation, recording, OCR and local library with sensible limits only where necessary.
- **Zn ip Pro:** low one-time or low annual price for advanced editor, local AI, unlimited local history and premium export presets.
- **Zn ip Cloud (optional):** transparent storage/egress pricing; never bundle unlimited storage into a low-price plan without usage guardrails.
- **Team:** priced per seat only when admin/SSO/SCIM and hosted collaboration are actually used.

Do not copy CleanShot's exact pricing; the strategic advantage is “more local capability for less, with cloud optional.”
