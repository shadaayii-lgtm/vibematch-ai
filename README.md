# VibeMatch — AI Style Transfer App

Upload a reference photo + your photo → AI transforms your look to match the reference vibe, outfit, and energy — without changing your face.

---

## How It Works

1. User uploads a **Reference Photo** (style they want)
2. User uploads **Their Photo** (their face is preserved)
3. **Claude AI** analyzes the reference image → extracts style, outfit, colors, lighting
4. **Replicate AI** applies that style to the user's photo using IP-Adapter (face-preserving model)
5. Result image is shown and downloadable

---

## Setup Instructions (Step by Step)

### Step 1 — Get Your API Keys

**Anthropic (Claude) API Key:**
1. Go to https://console.anthropic.com
2. Sign up for free
3. Go to "API Keys" → Create a new key
4. Copy it (starts with `sk-ant-...`)

**Replicate API Token:**
1. Go to https://replicate.com
2. Sign up for free (get $5 credit automatically)
3. Go to Account Settings → API Tokens
4. Copy your token

---

### Step 2 — Put the Code on GitHub

1. Go to https://github.com and sign up
2. Click **"New repository"**
3. Name it: `vibematch`
4. Set it to **Public**
5. Click **"Create repository"**
6. On the next page, click **"uploading an existing file"**
7. Upload ALL these files maintaining the folder structure:
   - `index.html`
   - `api/transform.js`
   - `vercel.json`
   - `README.md`
8. Click **"Commit changes"**

---

### Step 3 — Deploy on Vercel

1. Go to https://vercel.com and sign up with your GitHub account
2. Click **"Add New Project"**
3. Find your `vibematch` repo and click **"Import"**
4. Before clicking Deploy, click **"Environment Variables"**
5. Add these two variables:
   - Name: `ANTHROPIC_API_KEY` → Value: your Anthropic key
   - Name: `REPLICATE_API_TOKEN` → Value: your Replicate token
6. Click **"Deploy"**
7. Wait ~1 minute → You'll get a live URL like `vibematch.vercel.app` 🎉

---

### Step 4 — Choose the Right Replicate Model

In `api/transform.js`, replace the `version` string with one of these:

**Best option (face-preserving style transfer):**
- Go to https://replicate.com/tencentarc/photomaker-style
- Click "API" tab → copy the version hash
- Paste it as the `version` value in the API file

**Alternative:**
- https://replicate.com/zsxkib/instant-id

Update `api/transform.js` and the `input` parameters to match the model's expected inputs (shown on the model's page).

---

## File Structure

```
vibematch/
├── index.html          ← Frontend (upload UI + result display)
├── api/
│   └── transform.js    ← Backend (Claude + Replicate API calls)
├── vercel.json         ← Deployment config
└── README.md           ← This file
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML + CSS + Vanilla JS |
| Style Analysis | Claude AI (Anthropic) |
| Image Generation | Replicate (IP-Adapter) |
| Hosting | Vercel (free) |
| Code Storage | GitHub (free) |

---

## Cost Estimate

- Vercel hosting: **Free**
- GitHub: **Free**
- Anthropic (Claude): **Free tier** (limited requests/month)
- Replicate: **~$0.003–0.01 per image** ($5 free credit = ~500 images)
