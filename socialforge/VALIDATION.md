# Validation

Checks completed in Chrome:
- Sample product -> Instagram portrait generation -> preview: passed, 1080×1350.
- PNG export: passed; downloaded file independently decoded as PNG at 1080×1350.
- Image upload: passed; exported PNG selected through the file chooser and decoded successfully.
- YouTube thumbnail generation: passed, 1280×720 preview.
- Cancellation: passed; cancelled status appears and previous output remains available.
- Refresh and history restore: passed; completed results survive refresh in IndexedDB.
- node --check dist/app.js: passed.

Not exercised: every style/format combination, all invalid input cases, mobile browsers, storage quota failures, load and security testing. Source implements validation and storage failure handling, but these paths are not all manually tested. No live AI service is connected.
