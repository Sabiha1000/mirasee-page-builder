# Deployment Guide — Step by Step

This is the playbook for getting the Mirasee Page Builder live on GitHub Pages so your manager can use it.

---

## Step 1: Get the files onto your computer

Download all the files in this folder:
- `index.html`
- `README.md`
- `.nojekyll`
- `.gitignore`
- `DEPLOYMENT.md` (this file)

Put them in a folder on your computer named `mirasee-page-builder`.

---

## Step 2: Create a GitHub account (if you don't have one)

Go to [github.com](https://github.com) and sign up. Free tier is fine.

---

## Step 3: Create a new repository

1. Click the **+** in the top-right of GitHub → **New repository**
2. Repository name: `mirasee-page-builder`
3. Description (optional): "Copy-to-code agent for Mirasee landing pages"
4. Visibility: **Private** if you want only your manager to see it, **Public** if you want it freely accessible
5. **Don't** check "Add a README file" — you already have one
6. Click **Create repository**

---

## Step 4: Upload the files

GitHub will show you a page with two paths. Use the **easiest one**:

### Option A: Upload via web (easiest, no terminal needed)

1. On the new empty repo page, click **"uploading an existing file"** link
2. Drag all 5 files from your `mirasee-page-builder` folder into the browser
3. Scroll down, write a commit message like "Initial commit"
4. Click **Commit changes**

### Option B: Use Git (if you know it)

```bash
cd mirasee-page-builder
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/mirasee-page-builder.git
git push -u origin main
```

---

## Step 5: Enable GitHub Pages

1. In your repo, go to **Settings** (top tab)
2. Scroll down on the left sidebar → **Pages**
3. Under **Source**, select **Deploy from a branch**
4. Under **Branch**, select **main** and folder **/ (root)**
5. Click **Save**

GitHub will now build and deploy. After ~1 minute, refresh the Pages section. You'll see:

> Your site is live at `https://YOUR_USERNAME.github.io/mirasee-page-builder/`

---

## Step 6: Test it

1. Open the live URL
2. You'll see the Mirasee Page Builder interface
3. Get an API key from [console.anthropic.com](https://console.anthropic.com) → API Keys → Create Key
4. Paste the key into the bar at the top
5. Pick a template, paste copy, click Generate

---

## Step 7: Share with your manager

Send your manager:
- **The live URL:** `https://YOUR_USERNAME.github.io/mirasee-page-builder/`
- **The repo URL:** `https://github.com/YOUR_USERNAME/mirasee-page-builder` (so he can review the code)
- **A short note:** "He'll need his own Anthropic API key from console.anthropic.com to use it. The key stays in his browser only."

---

## If you hit problems

### "Page is blank when I open the URL"
- Make sure GitHub Pages is enabled (Step 5)
- Wait 1-2 more minutes — sometimes the first deploy takes a bit
- Hard-refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)
- Check the browser console (right-click → Inspect → Console) for errors

### "API call fails with CORS or 401 error"
- 401 = the API key is wrong or expired. Generate a new one.
- CORS errors shouldn't happen — the app uses the `anthropic-dangerous-direct-browser-access` header. If you see CORS errors, tell me and I'll investigate.

### "I want to change the Mirasee CSS"
- Edit `index.html`, find the `MIRASEE_CSS` constant near the top of the script
- Update the CSS string
- Commit and push — GitHub Pages auto-redeploys in ~1 minute

### "The AI is structuring my copy weirdly"
- Edit `index.html`, find `buildSystemPrompt()`
- Tweak the rules (e.g., add Mirasee-specific guidelines, change emphasis rules)
- Commit and push

---

## Cost expectations

- **GitHub Pages:** Free (forever, for this kind of project)
- **Anthropic API:** ~$0.01-$0.03 per page generation. A designer making 20 pages a month would spend under $1/month.
- **Custom domain (optional):** If you want `pagebuilder.mirasee.com` instead of the github.io URL, that's free to set up but you'd need DNS access.

---

## Updating the app later

Any time you want to change something:

1. Edit the files locally (or directly in GitHub by clicking the pencil icon on any file)
2. Commit changes
3. GitHub Pages auto-redeploys in ~1 minute
4. Refresh the live URL to see changes

That's it. Good luck.
