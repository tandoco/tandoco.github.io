# 🍳 tandoco Recipe Lab

A fully client-side recipe development tracker built for food businesses. Track recipes from idea to approval, log development notes, collect tester feedback via QR code, and monitor macro/protein targets — all without a backend or database.

**[→ Open the App](https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/)**

---

## ✨ Features

- **Recipe Pipeline** — Track every recipe through `Ideation → Testing → Refining → Approved / Rejected`
- **Macro Tracking** — Log calories, protein, carbs, and fat per recipe
- **Development Notes** — Add timestamped notes with author attribution
- **Tester Feedback** — Collect star ratings + comments from friends & family
- **QR Code Sharing** — Generate a scannable QR code so testers can submit feedback directly from their phone
- **Sidebar Filters** — Filter by status or browse all recipes at once
- **Search & Sort** — Find recipes instantly by name, category, or macro targets
- **Stats Dashboard** — At-a-glance counts for each pipeline stage
- **No backend required** — All data is stored in your browser's `localStorage`

---

## 🚀 Deploy to GitHub Pages (3 steps)

### 1. Create a repository

Go to [github.com/new](https://github.com/new) and create a new repository.  
You can name it anything — e.g. `recipe-lab`.

### 2. Upload the file

In your new repository, click **"uploading an existing file"** and upload `index.html`.  
Commit directly to `main`.

### 3. Enable GitHub Pages

1. Go to **Settings → Pages**
2. Under **Source**, select `Deploy from a branch`
3. Choose `main` branch, `/ (root)` folder
4. Click **Save**

Your site will be live at:
```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

> **Tip:** It can take 1–2 minutes for GitHub Pages to build after the first deploy.

---

## 📱 QR Code Feedback Flow

Each recipe has a **"Get QR Code"** button that generates a scannable code. When a tester scans it, they land on the feedback form for that specific recipe. The URL uses a `#feedback/RECIPE-ID` hash — no server needed.

To make this work correctly on your live site, just make sure you're sharing the **published GitHub Pages URL** (not a localhost link).

---

## 🗂 File Structure

```
/
└── index.html   ← The entire app (HTML + CSS + JS, self-contained)
```

No npm, no build step, no dependencies to install. Just one file.

---

## 💾 Data & Storage

All recipe data is saved in your browser's **localStorage** under the key `tandoco_recipes`.  
This means:
- Data persists across page refreshes ✅
- Data is **per-browser / per-device** — not synced across computers
- Clearing browser data will erase recipes — export regularly if needed

> Want cloud sync? The app can be extended to use a backend like Supabase or Firebase by replacing the `save()` / `load()` functions in the JavaScript.

---

## 🛠 Local Development

No setup required. Just open `index.html` directly in any modern browser:

```bash
# macOS
open index.html

# Windows
start index.html

# Or use a simple local server
npx serve .
```

---

## 📋 Recipe Fields

| Field | Description |
|-------|-------------|
| Name | Recipe title |
| Category | e.g. Breakfast, Snack, Dinner |
| Status | Ideation / Testing / Refining / Approved / Rejected |
| Target Protein | Grams of protein per serving |
| Calories | Kcal per serving |
| Carbs / Fat | Macros in grams |
| Servings | Number of servings |
| Description | Free-text overview |
| Ingredients | Ingredient list |
| Instructions | Step-by-step method |
| Notes | Internal development log (timestamped, with author) |
| Feedback | Tester ratings + comments (via QR or manual entry) |

---

## 🔧 Customization Tips

**Change the brand name/colors:**  
Edit the CSS variables at the top of `index.html`:
```css
:root {
  --primary: #E8703A;  /* Main orange accent */
  --primary-dark: #C85A28;
  --green: #2A7A4B;    /* Approved status */
  ...
}
```

**Change "tandoco Recipe Lab" to your brand:**  
Search for `tandoco` in `index.html` and replace with your business name.

---

## 📄 License

MIT — free to use, modify, and deploy for your business.
