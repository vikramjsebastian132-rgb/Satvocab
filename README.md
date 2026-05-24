# SAT Vocabulary Study App

A fully self-contained vocabulary study website with **Browse**, **Flashcards**, and **Quiz** modes — covering the 1,000 most common SAT words.

No frameworks, no dependencies, no build step. Just one HTML file.

---

## Features

- **Browse** — search any word or definition, filter by letter
- **Flashcards** — word → definition or definition → word; flip cards; mark known/unknown
- **Quiz** — multiple-choice quiz with custom letter selection, question count, and question type
- Missed word review at the end of every quiz

---

## Deploy to Railway in 5 steps

### Step 1 — Put it on GitHub

1. Go to [github.com](https://github.com) and sign in (or create a free account).
2. Click the **+** icon (top right) → **New repository**.
3. Name it `sat-vocab-app`, keep it **Public**, click **Create repository**.
4. On your computer, open a terminal in the folder where you saved this project, then run:

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/sat-vocab-app.git
git push -u origin main
```

> Replace `YOUR_USERNAME` with your actual GitHub username.

---

### Step 2 — Sign up for Railway

1. Go to [railway.app](https://railway.app).
2. Click **Start a New Project** → **Login with GitHub** and authorize Railway.

---

### Step 3 — Deploy from GitHub

1. On the Railway dashboard, click **New Project**.
2. Choose **Deploy from GitHub repo**.
3. Select **sat-vocab-app** from the list.
4. Railway will automatically detect it and start deploying.

---

### Step 4 — Tell Railway it's a static site

Since this is a plain HTML file, Railway needs a tiny config to serve it. Add a `railway.json` file to your project root:

```json
{
  "$schema": "https://railway.app/railway.schema.json",
  "build": {
    "builder": "NIXPACKS"
  },
  "deploy": {
    "startCommand": "npx serve . -p $PORT",
    "restartPolicyType": "ON_FAILURE"
  }
}
```

Then push it to GitHub:

```bash
git add railway.json
git commit -m "add railway config"
git push
```

Railway will automatically redeploy.

---

### Step 5 — Get your public URL

1. In Railway, click your project → **Settings** → **Domains**.
2. Click **Generate Domain** — you'll get a free URL like `sat-vocab-app.up.railway.app`.
3. Share that link with anyone!

---

## Local preview (optional)

Just open `index.html` directly in any browser — no server needed.

```bash
open index.html        # Mac
start index.html       # Windows
xdg-open index.html    # Linux
```

---

## Project structure

```
sat-vocab-app/
├── index.html      ← the entire app (HTML + CSS + JS, self-contained)
├── railway.json    ← Railway deploy config
└── README.md       ← this file
```

---

## Customizing the word list

All vocabulary words are stored as a JavaScript array near the top of `index.html`. Each entry looks like:

```js
{"w":"ebullient","p":"adj.","d":"extremely lively, enthusiastic","e":"She became ebullient upon receiving an acceptance letter from her first-choice college."}
```

- `w` = word
- `p` = part of speech
- `d` = definition
- `e` = example sentence

Add, remove, or edit entries freely.
