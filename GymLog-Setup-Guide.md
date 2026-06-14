# GymLog — Setup Guide

## How to use GymLog

GymLog is a single HTML file. Open it in Safari on your iPhone, add it to your Home Screen, and it works like an app. Each person connects their **own** Google Drive — your data stays yours.

---

## Step 1 — Add to iPhone Home Screen

1. Open `gym-tracker.html` in **Safari** (not Chrome)
2. Tap the **Share** button (box with arrow pointing up)
3. Scroll down and tap **"Add to Home Screen"**
4. Tap **Add** — it will appear on your home screen as "GymLog"

---

## Step 2 — Host the file (required for Google Drive)

Google's sign-in only works from an HTTPS page — it refuses connections from files opened directly. You need to host `gym-tracker.html` somewhere before Drive will connect.

### Netlify Drop (free, ~1 minute, no account needed)

1. On any computer, go to **[app.netlify.com/drop](https://app.netlify.com/drop)**
2. Drag `gym-tracker.html` onto the drop zone
3. You'll get a URL like `https://charming-fox-abc123.netlify.app` — copy it
4. That's your app URL. Open it on iPhone → Safari → Add to Home Screen

> **Sharing with others:** everyone uses the same URL but sets up their own Client ID and connects their own Drive. Data is completely separate.

---

## Step 3 — Get your Google OAuth Client ID

Each person needs their own Client ID. This is free and takes ~5 minutes.

### 2a — Create a Google Cloud project

1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Click **"Select a project"** → **"New Project"**
3. Name it `GymLog` → click **Create**

### 2b — Enable the Drive API

1. In the left menu, go to **APIs & Services → Library**
2. Search for **"Google Drive API"**
3. Click it → click **Enable**

### 2c — Create OAuth credentials

1. Go to **APIs & Services → Credentials**
2. Click **"+ Create Credentials"** → **"OAuth client ID"**
3. If prompted to configure the consent screen:
   - Choose **External** → **Create**
   - Fill in App name: `GymLog`
   - Fill in your email as support email
   - Click **Save and Continue** through all steps
   - On the last screen, click **Back to Dashboard**
4. Back in Credentials → **"+ Create Credentials"** → **"OAuth client ID"**
5. Application type: **Web application**
6. Name: `GymLog`
7. Under **Authorised JavaScript origins**, click **+ Add URI** and enter the URL where you'll open the app.
   - If opening from a local file or Home Screen PWA, add: `https://localhost` and also the domain if you host it anywhere.
   - For a simple local setup, add `null` or leave blank — the popup flow will still work on most devices.
8. Click **Create**
9. Copy your **Client ID** — it looks like `1234567890-xxxxx.apps.googleusercontent.com`

### 2d — Add yourself as a test user (while app is in testing)

1. Go to **APIs & Services → OAuth consent screen**
2. Scroll to **Test users** → click **+ Add Users**
3. Add your Gmail address (and your partner's/friend's Gmail too)
4. Click **Save**

---

## Step 4 — Enter your Client ID in the app

1. Open GymLog
2. Paste your Client ID in the setup screen
3. Tap **Get Started**
4. On the Settings screen, tap **Connect** next to Google Drive
5. Approve the Google sign-in prompt

**Your workouts will now automatically save to a `GymLog` folder in your Google Drive after each session.**

---

## Step 5 — Add to iPhone Home Screen

Open your Netlify URL in **Safari** → Share → **Add to Home Screen** → Add.

---

## Sharing with your partner or friend

Send them:
- The `gym-tracker.html` file (via AirDrop, iMessage, email)
- This setup guide

Each person follows the same steps above to create **their own** Client ID and connect **their own** Drive. Data is completely separate.

---

## Tips

- **Offline use:** The app works fully offline. Workouts save locally on your phone. They'll upload to Drive next time you're connected and signed in.
- **PRs:** The app automatically detects when you've beaten a personal record and highlights it during your session.
- **Programs:** Create a routine (e.g. Push Day) with your exercises, sets, and rep targets. Then hit "Start Session" and the exercises are pre-loaded.
- **Export:** Settings → Export all data gives you a JSON backup of everything.

---

*GymLog stores all data in your browser's local storage and your own Google Drive. No account, no subscription, no server.*
