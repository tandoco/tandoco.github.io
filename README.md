# 🧪 tandoco Recipe Lab

A fully client-side recipe development tracker for food businesses. Track recipes from ideation to approval, log development notes, collect tester feedback via public QR code, and monitor protein/macro targets — all hosted free on GitHub Pages.

**[→ Open the App](https://YOUR-USERNAME.github.io/)**

---

## 📁 Files

```
/
├── index.html       ← Main app (login required)
└── feedback.html    ← Public feedback form (no login — anyone can access)
```

---

## ✨ Features

- **Recipe Pipeline** — Track every recipe through `Ideation → Testing → Refining → Approved / Rejected`
- **Macro Tracking** — Log calories, protein, carbs, fat, and fiber per serving
- **Development Notes** — Timestamped internal notes with author attribution
- **Public Tester Feedback** — Anyone can scan a QR code and submit star ratings + comments, no login needed
- **Sync Feedback** — One-click button pulls all tester submissions from GitHub into the app
- **QR Code Generator** — Printable QR per recipe, links directly to `feedback.html`
- **Search, Sort & Filter** — By name, status, category, protein, or rating
- **Stats Dashboard** — At-a-glance pipeline counts
- **No backend required** — Main app uses `localStorage`; feedback uses GitHub Issues as a free database

---

## 🚀 Deploy to GitHub Pages

### Step 1 — Create the special root repo

Go to [github.com/new](https://github.com/new) and name the repository **exactly**:
```
YOUR-USERNAME.github.io
```
*(This naming makes GitHub Pages automatically serve it at your root URL)*

### Step 2 — Upload both files

In your new repo, click **"uploading an existing file"** and upload:
- `index.html`
- `feedback.html`

Commit to `main`.

### Step 3 — GitHub Pages is auto-enabled

For a `username.github.io` repo, Pages turns on automatically. Your site will be live at:
```
https://YOUR-USERNAME.github.io
```
*(Allow 1–2 minutes for first deploy)*

---

## 📱 Setting Up Public QR Feedback (One-Time, ~5 min)

Feedback is stored as GitHub Issues in a separate repo — completely free, no server needed.

### 1. Create a feedback repo

Go to [github.com/new](https://github.com/new) and create a **new public repo** named something like `recipe-feedback`.  
*(Keep it separate from your site repo)*

### 2. Create a Personal Access Token

1. Go to **github.com → Settings → Developer Settings → Personal Access Tokens → Fine-grained tokens**
2. Click **Generate new token**
3. Set expiration (1 year recommended)
4. Under **Repository access**, select **Only select repositories** → choose your `recipe-feedback` repo
5. Under **Permissions → Repository permissions**, set **Issues** to `Read and write`
6. Click **Generate token** and copy it (you won't see it again)

### 3. Add your credentials to both files

In **`feedback.html`**, find the CONFIG block near the top and fill in:
```javascript
const GITHUB_OWNER = 'your-username';      // Your GitHub username
const GITHUB_REPO  = 'recipe-feedback';    // The feedback repo name
const GITHUB_TOKEN = 'github_pat_...';     // Your token from step 2
```

Do the same in **`index.html`** (same three lines, same values — needed for the Sync button).

### 4. Redeploy

Upload both updated files to your GitHub Pages repo. Done!

---

## 🔄 How Feedback Flows

```
Tester scans QR  →  feedback.html opens  →  they submit rating + comment
                                                      ↓
                                          Creates a GitHub Issue in your
                                          recipe-feedback repo
                                                      ↓
                  You click "Sync Feedback" in the app header
                                                      ↓
                          Feedback appears in the recipe's Feedback tab
```

- Each tester submission = one GitHub Issue, tagged with the recipe ID
- The app de-duplicates on sync — safe to sync multiple times
- You can also read feedback directly in your GitHub Issues tab

---

## 💾 Data & Storage

| Data | Where it's stored |
|------|-------------------|
| Recipes, notes, local feedback | Browser `localStorage` on your device |
| Tester QR feedback | GitHub Issues (synced on demand) |

> **Important:** `localStorage` data is per-browser, per-device. It won't sync across your computers automatically. If you want cross-device access, consider exporting your data periodically.

---

## 🔧 Customization

**Change brand name / colors** — edit the CSS `:root` variables and search for `tandoco` in both files.

**Change the login password** — in `index.html`, find this line and update it:
```javascript
if (user === 'tandoco' && pass === 'cinnamonroll2001') {
```

---

## 📄 License

MIT — free to use, modify, and deploy.
