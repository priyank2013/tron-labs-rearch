# Video placement

Use this exact location for your own background loop:

- `assets/videos/tron-ai-sample.mp4`

The homepage reads the video in `index.html` inside the `VIDEO_REPLACE_START` / `VIDEO_REPLACE_END` block near the top of `<body>`.

Current behavior:
- Primary sample source (for immediate testing): `https://build.ai/center.mp4`
- Local replacement source: `assets/videos/tron-ai-sample.mp4`

When you add your own file, you can keep only the local source or move it to be the first `<source>`.
