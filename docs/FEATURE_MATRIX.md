# Znip Feature Matrix

Priority meanings: **P0 = launch-critical**, **P1 = competitive parity / early differentiation**, **P2 = power-user expansion**, **P3 = team/cloud/enterprise or later polish**.

| Priority | Area | Znip capability | Benchmark | Acceptance summary |
|---|---|---|---|---|
| P0 | Capture | Area, window, display, full-screen, timer | CleanShot + Shotbase | One shortcut opens capture UI; selection is pixel-accurate; output is immediately available in tray. |
| P0 | Capture | Window detection + transparent/background modes | CleanShot | Detect windows reliably; preserve rounded corners/shadow option; no accidental desktop clutter. |
| P0 | Capture | Quick Access Tray | CleanShot | Latest capture appears in corner; save/copy/reveal/edit/drag/share; tray can be dismissed and recovered. |
| P0 | Capture | All-in-one capture mode | CleanShot | One shortcut exposes area/window/fullscreen/record/scroll; remembers last region and aspect lock. |
| P0 | Annotation | Crop, arrow, line, rectangle, ellipse, text, pencil, highlight | Both | Non-destructive tools, keyboard navigation, undo/redo, retina-quality export. |
| P0 | Annotation | Secure redaction | CleanShot | Pixelate uses randomized blocks; blur has irreversible export path; redaction never leaks original pixels. |
| P0 | Annotation | Color picker and palette | CleanShot | Pick screen color; save/reorder favorites; accessible contrast preview. |
| P0 | Recording | Area/window/fullscreen screen recording | Both | Reliable long recording; pause/stop; handles display changes and sleep interruptions predictably. |
| P0 | Recording | System audio + microphone | CleanShot | Select sources independently; synchronized output; clear permission state and failure explanation. |
| P0 | Recording | MP4/GIF export | CleanShot | Presets for quality, FPS, dimensions, bitrate; export progress/cancel/retry. |
| P0 | Privacy | Local-first storage | Shotbase | No capture upload by default; explicit upload boundary; offline capture/edit works. |
| P0 | Library | Local capture history | Both | Unified screenshots/recordings/web captures; thumbnails; dates; type filters; reveal/delete. |
| P0 | Settings | Global shortcuts and output defaults | CleanShot | Conflict detection; per-action shortcut; save/copy/clipboard/file format settings. |
| P1 | Capture | Scrolling capture vertical + horizontal | CleanShot | Works in common browsers, documents and chats; stitch preview; cancel/retry; transparent failure mode. |
| P1 | Capture | Crosshair, magnifier, freeze screen | CleanShot | Magnifier follows pointer; freeze captures moving UI; crosshair shows dimensions/coordinates. |
| P1 | Annotation | Counter, spotlight, smart highlighter, text styles | CleanShot | Tutorial-quality annotations with consistent geometry and editable properties. |
| P1 | Annotation | Combine images / composition canvas | CleanShot | Drag images into editor; layer order, alignment, snapping, resize, export. |
| P1 | Annotation | Backgrounds, frames, shadows, padding, aspect presets | Both | Reusable style presets; auto-balance; social presets; transparent background support. |
| P1 | Recording | Click highlights + keystroke overlays | CleanShot | Configurable color/size/style/animation; command-only option; timeline-aware rendering. |
| P1 | Recording | Webcam bubble | CleanShot | Position, size, shape, fullscreen; camera permission and device selection. |
| P1 | Recording | Editable project files | CleanShot | Reopen capture with annotations/effects editable; versioned, portable project format. |
| P1 | Editor | Smart zooms / cursor smoothing | Both | Add keyframes or auto-detect; preview quality; adjustable easing and cursor treatment. |
| P1 | Editor | Motion blur + 3D/perspective | Both | Optional effects with GPU fallback; predictable export; no forced gimmicks. |
| P1 | Web | Full-page/viewport web capture | Shotbase | URL, breakpoint, light/dark mode, page height; document cookies/security behavior. |
| P1 | OCR | On-device OCR to clipboard | CleanShot | Region select → recognized text; language selection; no remote pixels; confidence/format handling. |
| P1 | AI | Local smart filenames/tags/summaries | Shotbase | Apple-silicon local model; queue/cancel; opt-out; derived metadata deletion; no analytics leakage. |
| P1 | Search | Smart local search | Both | Search filename, tags, OCR, summary, transcript; instant index updates; offline. |
| P1 | Sharing | Optional one-click hosted link | Both | Upload only after explicit action; clean link; expiry/password later; recipient needs no app. |
| P2 | Editor | Social exports landscape/square/vertical | CleanShot | Presets for 16:9, 1:1, 9:16; safe areas; background and caption options. |
| P2 | Editor | Video transcription and captions | CleanShot | On-device first; editable transcript; subtitle burn-in/export; speaker/audio handling. |
| P2 | Library | Reminders and capture inbox | Shotbase | Scheduled reminders; snooze; clear notification rationale; no nagging default. |
| P2 | Library | Saved searches, tags, collections | Both | Smart folders; manual collections; batch tag/rename/archive. |
| P2 | Library | Floating screenshots / always-on-top references | CleanShot | Pin/unpin; opacity; click-through; screen-aware positioning. |
| P2 | Library | Hide desktop icons | CleanShot | Temporary reversible hide with restore after capture/record. |
| P2 | Extensibility | URL scheme / automation | CleanShot ecosystem cue | Document actions for capture, open library, export, share; safe parameter validation. |
| P2 | Reliability | Device/display/audio resilience | Shotbase changelog cue | Test unplug/replug, sleep, permission changes, display scaling, low disk, long recordings. |
| P3 | Cloud | Searchable hosted library | CleanShot | Search transcripts/content/tags; media lifecycle; download/export all. |
| P3 | Cloud | Link expiry, password, access controls | CleanShot | Privacy defaults; revoke; audit; clear public/private state. |
| P3 | Cloud | Comments/reactions | Both | Threaded comments attached to media/time; notifications optional. |
| P3 | Teams | Custom domain/branding | Both | Brand links and pages without exposing Znip internals. |
| P3 | Teams | SSO/SCIM/admin/team seats | CleanShot | Enterprise identity and lifecycle; independent from local-only app. |

## Definition of “on par”

- Capture latency feels instant on current Apple silicon.
- No lost capture during permissions, display changes, sleep or low-disk states.
- Every destructive privacy action is technically irreversible in exported output.
- Local capture/edit/OCR/search works without an account or network.
- Exported output has no visible quality regression against reference screenshots/videos.
- Keyboard-first path is complete; mouse-only UI is never required.
