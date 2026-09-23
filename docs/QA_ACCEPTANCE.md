# Znip QA and Acceptance Pack

## Capture matrix

Test each capture mode on one display, two displays, mixed scaling, Retina and non-Retina, light/dark mode, Stage Manager on/off, fullscreen app, menu-bar app, browser, video, code editor, long chat and high-motion content.

- Area selection starts, moves, resizes, cancels and preserves aspect lock.
- Window selection chooses the intended window even with overlapping windows.
- Fullscreen/display capture names the correct display.
- Timer can cancel without leaving a stale overlay.
- Copy/save/drag produce the same pixels and metadata expected.
- Quick Access Tray never obscures the captured content or steals focus unexpectedly.

## Privacy/redaction tests

- Capture a password-like string, apply pixelate, export, reopen exported file and verify the original cannot be recovered.
- Apply blur and verify secure mode rasterizes the redaction.
- Turn local AI off, capture content, inspect network activity and verify no AI request occurs.
- Capture while offline; capture, edit, OCR, search and export must continue.
- Create a share link only after explicit action; verify the library item shows a cloud/upload state.

## Recording tests

- System audio only, microphone only, both, neither.
- Camera permission denied, camera unplugged, camera in use by another app.
- Display unplugged mid-recording.
- Sleep/wake during recording.
- Low disk space.
- 4K/high-DPI screen.
- Pause/resume, cancel, crash recovery, partial-file cleanup.
- Cursor/click/keystroke overlays are synchronized and disappear when disabled.
- MP4/GIF exports open in QuickTime and browser.

## Editor tests

- Undo/redo every annotation and property change.
- Reopen an editable project after app restart.
- Resize canvas and preserve vector geometry.
- Export at 1x/2x/3x and verify no fuzzy text.
- Test background auto-balance with narrow, wide, transparent and shadowed windows.
- Test video zoom keyframes, trim, cursor smoothing and motion blur.
- Export landscape/square/vertical without clipping.

## Library/search tests

- Index screenshot text, OCR text, tags, summary, filename and transcript.
- Search offline and during background indexing.
- Delete original vs project vs derived metadata.
- Batch rename/tag/archive.
- Corrupt/missing asset produces a recoverable state, not a crash.
- Import/export library backup.

## Accessibility and native behavior

- Full keyboard operation.
- VoiceOver labels for every control.
- Reduce Motion and Increase Contrast.
- Menu-bar-only launch and login-item behavior.
- Respect system appearance and accent color without sacrificing contrast.
- App sandbox, notarization, hardened runtime and permission descriptions.
