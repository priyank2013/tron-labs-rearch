# Video placement

Use this exact location for your own first-screen background loop:

- `assets/videos/tron-ai-sample.mp4`

The source is used in `index.html` inside the `VIDEO_REPLACE_START` / `VIDEO_REPLACE_END` block.
This block sits right after `<div class="bg-grid">` near the top of `<body>`.

Current behavior:
- Primary source: `https://build.ai/center.mp4` (for instant preview)
- Local source: `assets/videos/tron-ai-sample.mp4` (your replacement path)

To fully switch to your own file, remove the external source line and keep only the local source.
