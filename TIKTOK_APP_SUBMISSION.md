# TikTok App Submission Guide

This document contains all the information you need to submit your TikTok developer app for approval.

## Step 1: Host the Documentation Site

You need to host the HTML files online. Easiest options:

### Option A: GitHub Pages (Recommended)
1. Create a new GitHub repository (e.g., `makeit-docs`)
2. Copy the files from `docs/tiktok-app/` to the repository
3. Go to repository Settings → Pages
4. Set Source to "Deploy from a branch" and select `main`
5. Your URLs will be: `https://YOUR-USERNAME.github.io/makeit-docs/`

### Option B: Netlify Drop
1. Go to https://app.netlify.com/drop
2. Drag and drop the `docs/tiktok-app/` folder
3. You'll get instant URLs

---

## Step 2: Fill in the TikTok App Form

### Description (120 chars max)
```
A personal desktop app that converts gaming clips to vertical format and posts them to TikTok automatically.
```

### Terms of Service URL
```
https://ghasemikasra39.github.io/makeit-docs/terms.html
```

### Privacy Policy URL
```
https://ghasemikasra39.github.io/makeit-docs/privacy.html
```

### Platform
Select: **Desktop**

### App Review Explanation (1000 chars max)
```
MakeIt is a personal desktop application for macOS that automates gaming content posting.

How it works:
1. User runs the app locally on their Mac
2. App processes gameplay recordings and creates vertical 9:16 clips
3. Clips are temporarily uploaded to AWS S3
4. App uses TikTok Content Posting API to post via presigned URL
5. S3 files are deleted after successful posting

Scopes requested:
- video.upload: Required to upload video files to TikTok
- video.publish: Required to publish the uploaded videos

This is a personal automation tool. It only posts to my own TikTok account. No third-party users or multi-account functionality.

Integration flow:
1. App authenticates via OAuth 2.0 (tokens stored locally)
2. User triggers cross-posting after editing a gaming video
3. App converts highlight clips to 9:16 vertical format
4. App uploads to TikTok with auto-generated gaming captions
5. App records post history in local database

No user data is collected. All credentials stored locally on user's machine.
```

---

## Step 3: Create Demo Video

TikTok requires a demo video showing the integration. Here's what to demonstrate:

### Demo Video Script (2-3 minutes)

**Part 1: Show the Application (30 sec)**
- Open Terminal on macOS
- Show the config.yaml with TikTok settings (blur any real keys)
- Show cross_posting enabled in config

**Part 2: Show the Pipeline Running (1 min)**
- Run the social preview command on a gaming video:
  ```bash
  python -m ps5_pipeline.social_preview /path/to/gaming_video.mp4
  ```
- Show the vertical 9:16 clip being generated
- Show the output file in Finder

**Part 3: Show TikTok Posting Flow (1 min)**
- Show the console output of the pipeline posting to TikTok
- (If in sandbox) Show the sandbox TikTok account receiving the post
- Show the post appearing in TikTok (or the API success response)

**Part 4: Show Privacy/Terms (15 sec)**
- Open browser and show the hosted Terms of Service page
- Show the hosted Privacy Policy page

### Recording Tips
- Use QuickTime Player or OBS to screen record
- Keep under 50MB (use lower resolution if needed)
- Export as MP4
- Make sure text is readable

---

## Step 4: Products and Scopes to Request

On the TikTok developer portal, add these:

### Products
- **Content Posting API** ✓

### Scopes (under Content Posting API)
- `video.upload` - Upload videos to TikTok
- `video.publish` - Publish uploaded videos

**Do NOT request scopes you don't need** - this delays review.

---

## Step 5: Sandbox Testing (Before Submission)

TikTok requires you to test in sandbox mode first:

1. In the TikTok Developer Portal, find your app's sandbox credentials
2. Create a sandbox test user
3. Update your `secrets.yaml` with sandbox credentials
4. Run the pipeline and verify it works in sandbox
5. Record your demo video using sandbox

---

## After Submission

- Review typically takes 1-2 weeks
- Posts will be **private (SELF_ONLY)** until full audit approval
- You may receive requests for clarification - respond promptly

---

## File Checklist

```
docs/tiktok-app/
├── index.html      ✓  Main landing page
├── terms.html      ✓  Terms of Service
├── privacy.html    ✓  Privacy Policy
└── TIKTOK_APP_SUBMISSION.md  ✓  This guide
```

All files created and ready to deploy!
