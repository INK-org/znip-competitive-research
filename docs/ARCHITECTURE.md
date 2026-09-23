# Znip Architecture Direction

## Native stack

Recommended starting point: Swift + SwiftUI/AppKit with CoreGraphics, ScreenCaptureKit, AVFoundation, Vision/VisionKit, Core Image, Metal where needed, and a local persistence layer (SwiftData or SQLite behind a repository protocol).

Use AppKit where macOS behavior matters: menu-bar agent, global hotkeys, NSPanel/overlay windows, always-on-top floating captures, drag sources, pasteboard integration, login item and permission flows.

## Modules

- `CaptureCoordinator` — area/window/display/fullscreen/timer/all-in-one state machine.
- `SelectionOverlay` — crosshair, magnifier, dimensions, aspect lock and freeze.
- `ScreenCaptureService` — ScreenCaptureKit frame/audio acquisition.
- `WindowResolver` — visible window list, shadow/transparent capture and display mapping.
- `ScrollCaptureEngine` — controlled scroll sampling, stitching, overlap detection and failure recovery.
- `WebCaptureService` — local WKWebView renderer first; explicit URL/cookie/remote policy.
- `AnnotationModel` — versioned scene graph with vector annotations and redaction primitives.
- `StillEditor` — canvas/layers/undo/redo/export.
- `RecordingEditor` — timeline, tracks, effects, zoom/cursor/camera/audio.
- `RenderEngine` — still/video export, Metal/Core Image/AVAsset pipeline.
- `OCRService` — Vision text recognition and clipboard output.
- `LocalAIService` — model lifecycle, Apple-silicon acceleration, queue, opt-out, derived metadata.
- `LibraryStore` — media records, thumbnails, tags, OCR, summaries, projects and collections.
- `SearchIndex` — local full-text index with content-derived fields.
- `TrayController` — quick access overlay, drag/drop, action routing.
- `ShareService` — optional cloud adapter with explicit upload confirmation.
- `SettingsStore` — shortcuts, formats, destinations, permissions, privacy, AI and share defaults.

## Scene model

A capture should be represented as a source plus a non-destructive scene:

```text
CaptureAsset
  id, type, sourceURL, createdAt, displayID, scale, dimensions
  originalMediaReference
  sceneVersion
  annotations[]
  effects[]
  metadata { ocr, tags, summary, transcript }
  privacy { redactionsApplied, cloudUploaded, excludedFromAI }
```

Use immutable edit commands for undo/redo. A redaction layer must be marked as “secure export required”; the UI must not imply that a translucent blur is secure.

## Privacy invariants

- No upload on capture.
- No remote AI for local features.
- No capture contents in analytics.
- Share is an explicit user action and shows the destination.
- Public links warn that recipients can copy content.
- Local delete has a clear “delete original/project/derived metadata” choice.
- Sensitive media is never sent to crash logs.
- Permissions are requested just in time and explained in product language.

## Performance targets

- Overlay visible within 150 ms of shortcut on a warm app.
- First screenshot available within 500 ms after selection on modern Apple silicon.
- Tray interaction never blocks capture rendering.
- History thumbnail generation is background work.
- Long recording writes incrementally and survives interruption.
- Scroll capture gives progress and supports cancellation.
- Search results appear as the user types without main-thread stalls.
