# Static Page → Cloudflare Pages

A playful, colorful single-file landing page (`index.html`) ready to deploy on
**Cloudflare Pages** with automatic redeploys from **GitHub**.

## Files

- `index.html` — the page itself (HTML + inline CSS + JS, no build step).
- `.gitignore` — keeps OS junk out of the repo.

## One-time setup

### 1. Create a Cloudflare account
1. Go to <https://dash.cloudflare.com/sign-up>.
2. Sign up with your email and verify it.
3. The free plan is all you need for Pages.

### 2. Put this folder on GitHub
You only need to do this once.

```bash
# from this folder
git init
git add .
git commit -m "Initial commit: playful landing page"
git branch -M main
```

Create an empty repo on GitHub (https://github.com/new) — *do not* add a README
or .gitignore from GitHub; this folder already has them. Then:

```bash
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

### 3. Connect the repo to Cloudflare Pages
1. In Cloudflare Dashboard, open **Workers & Pages → Create → Pages → Connect to Git**.
2. Authorize the **Cloudflare Pages** GitHub app and pick this repo.
3. **Build settings:**
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Build output directory: `/`
4. Click **Save and Deploy**. First deploy takes ~30 seconds.

Cloudflare gives you a free `*.pages.dev` URL. Every `git push` to `main`
triggers a fresh deploy automatically.

## Making changes

```bash
# edit index.html
git add index.html
git commit -m "Update headline"
git push
```

Cloudflare detects the push and ships the new version in seconds.

## Custom domain (optional)

In your Pages project → **Custom domains → Set up a custom domain**.
Cloudflare will guide you through DNS — if your domain is already on Cloudflare,
it's a one-click setup.
