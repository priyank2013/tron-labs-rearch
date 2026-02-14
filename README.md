# Tron Labs Landing Page

Static landing page for Tron Labs (`index.html` + `styles.css`) with a Build.ai-style first-screen background video.

## Project Structure

- `index.html` — page structure and content.
- `styles.css` — styles and layout.
- `assets/videos/README.md` — exact video replacement path and notes.

## Run Locally

Because this is a static site, any basic HTTP server works.

```bash
python3 -m http.server 4173
```

Open: `http://localhost:4173`

## Video Source (Important)

The hero background video source is in `index.html` inside the `VIDEO_REPLACE_START` / `VIDEO_REPLACE_END` block.

Current setup:
- remote sample source: `https://build.ai/center.mp4`
- local replacement path: `assets/videos/tron-ai-sample.mp4`

If you upload your own video, keep only the local source line.

---

## Deploying on GCP (Firebase Hosting)

If your existing website is already hosted in Firebase on GCP, deploy this static site to the same project.

> Note: **Firestore** is a database service. Website hosting is done with **Firebase Hosting**. You can still use the same GCP/Firebase project where Firestore already exists.

### 1) Install Firebase CLI

```bash
npm install -g firebase-tools
```

### 2) Login and select your existing project

```bash
firebase login
firebase projects:list
firebase use <your-firebase-project-id>
```

### 3) Add Firebase hosting config in this repo

Run once:

```bash
firebase init hosting
```

Use these answers:
- **Use an existing project** → select your current project id
- **Public directory** → `.`
- **Configure as a single-page app** → `No` (this site is plain static HTML)
- **Set up automatic builds and deploys with GitHub** → optional
- **Overwrite `index.html`** → `No`

This creates `firebase.json` and `.firebaserc`.

### 4) Recommended `firebase.json`

Use this config to avoid deploying `.git`, docs, and local artifacts:

```json
{
  "hosting": {
    "public": ".",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**",
      ".git/**",
      "README.md"
    ]
  }
}
```

### 5) Deploy

```bash
firebase deploy --only hosting
```

After deploy, Firebase prints your Hosting URL.

---

## Deploy to Existing Custom Domain

If your domain is already attached to the same Firebase project, new deploys update it automatically.

If needed, verify domain mapping:
1. Firebase Console → Hosting → your site.
2. Check that `mytronlabs.com` (or desired subdomain) is connected.
3. Confirm DNS records match Firebase instructions.

---

## Optional: Keep Firestore in the Same Project

No extra changes are required for this static landing page to coexist with Firestore.
If later you add dynamic features, you can connect Firebase SDK and read/write Firestore from the same hosted site.
