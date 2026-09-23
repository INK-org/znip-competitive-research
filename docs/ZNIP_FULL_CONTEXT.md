# Znip — Full Context for an Agentic IDE

## 1. Original ask

Build Znip, a native macOS application at `znip.app`, to take on CleanShot X and Shotbase. Research both products comprehensively, prioritize the features, preserve privacy, undercut price, and deliver quality at least on par with them while exceeding them in selected areas.

## 2. Source of truth

This repository is the source of truth for the benchmark research:

- `docs/FEATURE_MATRIX.md`
- `docs/PRIORITY_ROADMAP.md`
- `docs/ARCHITECTURE.md`
- `docs/QA_ACCEPTANCE.md`
- `docs/SHOTBASE_RESEARCH.md`
- `docs/CLEANSHOT_RESEARCH.md`
- `sources.md`

## 3. Confirmed competitor surface

Shotbase: screenshots, video recording, scrolling capture, full-page/viewport web capture, responsive breakpoints, light/dark web mode, editor with background/frame/shadow/border/watermark/annotation/callout, automatic zooms, 3D/perspective, unified library, smart names, auto tags, summaries, search, local AI, reminders, capture tray/history, and optional sharing. Public local-AI promise: image analysis stays on Apple silicon; no automatic upload for ordinary local capture.

CleanShot: area/window/fullscreen/timer/scrolling capture, crosshair/magnifier/freeze, window background/transparent/shadow, All-In-One mode, Quick Access Overlay, annotation tools, secure pixelate/blur, color palette, composition, editable projects, recording/GIF/audio/camera/clicks/keystrokes, Studio Mode with zooms/cursor smoothing/motion blur/social exports, OCR on-device, history, floating screenshots, hide desktop icons, Cloud links, search/transcripts/tags, comments, expiration/passwords, branding, teams, SSO and SCIM.

## 4. Product thesis

Zn ip should be the **local-first capture workspace**: fastest capture path, best annotation and redaction, studio-quality recording editor, powerful offline library/search, private local AI, and optional sharing. The product should never force a cloud account for core capture, editing, OCR, search or export.

Differentiation opportunities:

- More complete local-first feature set than both competitors.
- Stronger privacy UX: visible upload boundaries, no-content analytics, secure redaction proof, local AI controls.
- One coherent scene/timeline model rather than separate screenshot and video tools.
- Better automation and recovery: shortcuts, URL scheme, scripting, display/audio resilience.
- Lower total price and transparent cloud usage.
- Accessibility, keyboard control and reduced motion as launch requirements.

## 5. Build order

### P0 launch spine

Native menu-bar app; permissions onboarding; area/window/display/fullscreen/timer; All-In-One; Quick Access Tray; history; core annotations; secure blur/pixelate; reliable video recording; system/mic audio; MP4/GIF; global shortcuts; offline-first storage; crash-safe recovery.

### P1 parity + moat

Scrolling capture; crosshair/magnifier/freeze; background tool; editable project files; webcam/click/keystrokes; Studio editor; web capture; OCR; local AI filenames/tags/summaries; smart search; optional share.

### P2 power users

Social exports; transcription/captions; collections/saved searches; floating references; hide desktop icons; reminders; batch operations; URL scheme; resilience hardening.

### P3 optional service

Cloud library; expiry/password/revoke; comments; branding/custom domain; team seats; SSO/SCIM.

## 6. Architecture

Use Swift + SwiftUI/AppKit. Use ScreenCaptureKit, AVFoundation, Vision/VisionKit, Core Image, Metal where required, and SwiftData/SQLite behind repository protocols. Keep capture, library, editor, local AI and optional sharing modular.

Core modules: CaptureCoordinator, SelectionOverlay, ScreenCaptureService, WindowResolver, ScrollCaptureEngine, WebCaptureService, AnnotationModel, StillEditor, RecordingEditor, RenderEngine, OCRService, LocalAIService, LibraryStore, SearchIndex, TrayController, ShareService, SettingsStore.

## 7. Non-negotiable safety invariants

- No upload at capture time.
- No capture pixels, OCR or filenames in analytics.
- No remote AI for local AI features.
- Share requires explicit confirmation and shows destination.
- Secure redaction must rasterize/replace original pixels in exported output.
- Local capture/edit/OCR/search/export works offline.
- Long recordings write incrementally and recover after interruption.
- Permissions are requested just in time.
- Sensitive media never appears in crash logs.

## 8. Builder instructions

Implement vertical slices, not disconnected mock screens. Each slice must include model, UI, native integration, failure state, keyboard path, accessibility, tests and a small demo fixture.

Start with P0 capture spine. Do not begin with cloud, marketing pages or a decorative dashboard. Do not use a generic web wrapper for the core capture surface. Preserve original Znip terminology and visual identity; do not copy competitor assets or UI.

Every feature should answer:

1. What is the keyboard-first happy path?
2. What is the permission-denied path?
3. What happens offline?
4. What happens when the display/audio/camera changes?
5. Is the output reversible/editable?
6. What is stored locally and what can leave the Mac?
7. How is it tested on Retina, multi-display and reduced-motion settings?

## 9. First demo success criteria

A fresh install can:

1. Complete a permission explanation flow.
2. Press one shortcut and capture an area/window/full screen.
3. Annotate with arrow/text/highlight and secure redaction.
4. Copy, save and drag the result to another app.
5. Record a 30-second clip with system audio and microphone.
6. Export MP4 and GIF.
7. Find both assets in offline history.
8. Run OCR locally and search for recognized text.
9. Restart the app and reopen an editable project.
10. Demonstrate that no account/network is required for all steps above.

## 10. Paste-ready builder prompt

You are building Znip, a native macOS capture workspace. Read every file in this repo before coding, especially `docs/FEATURE_MATRIX.md`, `docs/ARCHITECTURE.md`, and `docs/QA_ACCEPTANCE.md`. Implement the current roadmap phase as a real vertical slice in Swift + SwiftUI/AppKit, not a static prototype. Keep the core local-first and offline-capable. Never upload capture content without an explicit share action. Never send capture pixels, OCR text or filenames to analytics. Use native macOS APIs and honor permissions, multi-display, Retina, keyboard, VoiceOver and Reduce Motion. Add tests and a manual verification checklist. Report files changed, commands run, test results, known gaps and the next smallest vertical slice.

## 11. Review prompt

Review the implementation against this repository. Return exactly `READY` or `HOLD` first. If HOLD, list each blocker with: evidence/file, why it matters, exact fix, and test proving the fix. Pay special attention to accidental uploads, insecure redaction, lost recordings, main-thread capture work, permission loops, keyboard/accessibility failures, and divergence from the feature matrix.

## 12. Open questions

- Existing Znip codebase and chosen minimum macOS version.
- One-time vs subscription vs hybrid pricing.
- Cloud provider and jurisdiction, if sharing is offered.
- Whether Intel Macs receive local AI or only the non-AI product.
- Web capture privacy model for authenticated pages.
- Whether Znip supports iPhone/iPad capture later.
- Desired import compatibility with CleanShot projects.
