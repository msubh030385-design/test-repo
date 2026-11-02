# SocialForge — Social Media Content Studio

Assessment implementation prepared with an AI coding assistant. Review the source and adapt these notes before presenting this as your work.

## Run locally
Requires Python 3, or any static HTTP server. No package installation, API key, or build is required.

    python3 -m http.server 8080 --directory dist

Open http://localhost:8080. Use the sample product or upload JPG, PNG or WebP up to 8 MB and 25 megapixels. Configure the creative, generate, preview, download PNG. Select a recent creation to restore it after refresh.

## Scope and architecture
Vanilla JavaScript, HTML and CSS. Browser File API decodes local uploads; Canvas 2D composes a real PNG at the configured dimensions. IndexedDB stores up to six recent results locally. Static hosting serves the application; no backend or third-party generation service is called. Google Fonts is optional; system fallbacks work without it.

Formats: Instagram portrait 1080×1350, square 1080×1080 and story 1080×1920; TikTok vertical image 1080×1920; YouTube thumbnail 1280×720 and Shorts cover 1080×1920. These are explicit product presets, not a claim of exhaustive or current platform publishing requirements.

## Real versus simulated
REAL: file decoding, validation, image composition, format selection, PNG export, preview, local persistence, cancellation and errors.
SIMULATED: AI/model generation and the brief staged progress messages. Composition uses deterministic templates and user-written copy. It does not generate new product imagery or infer product details. The interface discloses demo mode.
NOT IMPLEMENTED: URL ingestion, video uploads/outputs, social posting, authentication, cloud storage, real LLM/image APIs, server jobs.

## Decisions and trade-offs
A complete image workflow was prioritized over incomplete multimodal breadth. Local composition avoids credentials, API cost, data transmission and provider failure. Contain scaling preserves the whole product rather than cropping it. Local persistence survives refresh, but is device/browser scoped and not an account-based service. Active jobs do not survive refresh and are not durable server jobs. Historical results survive when browser storage is available. Old output remains downloadable after a cancelled job.

## Security and reliability
No uploaded images leave the browser. File type, byte size and decoded pixel size are checked. User text is rendered through Canvas or textContent, not HTML insertion. Object URLs are revoked. No secrets are stored in source. There is no URL fetch endpoint (avoiding an SSRF surface). IndexedDB failure leaves download functional. Static host handles TLS. This is an assessment MVP, not a production-hardened multi-user platform.

## Next improvements
1. Add a server-only provider adapter with secrets, request limits and content safeguards.
2. Persist jobs in a database; queue workers with explicit queued/running/succeeded/failed states, retry limits, idempotency and timeouts; store outputs in object storage.
3. Add authentication, per-user quotas, retention policies, signed URLs, structured logs and metrics.
4. Add automated browser coverage, mobile/accessibility testing, layout-safe typography for long unbroken words and image-processing workers.
5. Add safe URL extraction with strict egress rules and later video rendering, based on user demand.

## Repository structure
- dist/index.html: accessible form and preview structure
- dist/style.css: responsive studio design
- dist/app.js: validation, rendering, async flow and IndexedDB
- IMPLEMENTATION_NOTES.md: submission disclosure and checks
- DEMO_SCRIPT.md: under-five-minute recording plan

## Ownership disclosure
Built with ChatGPT/Codex assistance. The candidate should be able to explain the renderer, asynchronous state, storage, limitations and future production design. No employment/project experience is implied by this prototype.
