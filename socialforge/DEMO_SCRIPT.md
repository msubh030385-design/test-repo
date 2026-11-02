# Demo walkthrough — target 4 minutes

0:00–0:25 — Introduce scope
“This is SocialForge. It converts a product photo into a downloadable social media creative. I focused on a complete image workflow. This assessment edition uses simulated AI generation, clearly labelled in the interface; the PNG composition and download are real.”

0:25–1:15 — Input and configuration
Upload a product JPG/PNG/WebP from your computer, or click Try with sample product. Edit the product name, headline and call to action. Choose a visual style. Explain the input limits: 8 MB and 25 megapixels.

1:15–2:00 — Generate and download
Select Instagram, portrait 4:5. Click Generate. Show progress and the 1080×1350 preview. Download the PNG and open it to show the actual output. Explain that aspect ratio and pixel dimensions are applied by the renderer.

2:00–2:35 — Another format and persistence
Select YouTube thumbnail, generate the 1280×720 asset. Refresh the page and restore a recent creation. Explain that history is stored on the device using IndexedDB; active jobs do not survive refresh.

2:35–3:10 — Failure handling
Start generation and cancel it. Explain that prior output is preserved. Mention invalid file, oversized file and decode errors; storage failure does not prevent downloading.

3:10–4:00 — Architecture, trade-offs and next steps
Show app.js and README. Explain File API → Canvas renderer → PNG and IndexedDB history. Mention AI coding assistance. Explain that a live provider would need server-side secrets, durable queued jobs, retries, object storage and quotas. URL ingestion and video are future work.

Record a real screen walkthrough using your preferred screen recorder. Keep under five minutes. Do not claim a real AI model, server queue or cloud persistence exists.
