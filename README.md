# UCSB Lambda Chi Alpha — Zeta Eta Zeta Site

Static site rebuild of ucsblambdachi.org, ready for GitHub Pages.

## What's here

- `index.html` — homepage (About House Corp, Leadership Event, Board, Recolonization CTA)
- `portal.html` — Alumni Portal "coming soon" placeholder (real member portal is phase 2)
- `assets/style.css` — all styling (purple/gold palette matching the chapter's colors)
- `assets/main.js` — mobile nav toggle + footer year

## Before you launch

`index.html` and `portal.html` already reference local paths (`assets/logo.png`, `assets/shield.png`, `assets/house.jpg`) — drop your three downloaded images into `assets/` with those exact filenames.

**Two new images are still hotlinked** from the old site (Ron Wolfe's Order of Merit photos, added Aug 2026 — not part of the original three-image set):
   - `assets/ron-wolfe-award.jpg` ← `https://ucsblambdachi.org/wp-content/uploads/sites/9669/2026/08/unnamed-1.jpg`

Download that one too, save it as `assets/ron-wolfe-award.jpg`, and update the `<img src>` in the "Alumni Spotlight" section of `index.html` to `assets/ron-wolfe-award.jpg` before cutover.

## Deploying to GitHub Pages

1. Create a new repo (e.g. `ucsblambdachi-site`) on GitHub
2. Push this folder as the repo root:
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR-ORG/ucsblambdachi-site.git
   git push -u origin main
   ```
3. In the repo: **Settings → Pages → Source → Deploy from branch → main / (root)**
4. GitHub will give you a `https://YOUR-ORG.github.io/ucsblambdachi-site/` URL

## Pointing ucsblambdachi.org at GitHub Pages

1. In the repo, add a file named `CNAME` (no extension) containing just:
   ```
   ucsblambdachi.org
   ```
2. At your domain registrar, update DNS:
   - **A records** for the apex domain (`ucsblambdachi.org`) pointing to GitHub's IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Or a **CNAME** for `www.ucsblambdachi.org` → `YOUR-ORG.github.io`
3. Back in Settings → Pages, set the custom domain to `ucsblambdachi.org` and enable "Enforce HTTPS" once it's verified

DNS changes can take a few hours to propagate.

## Phase 2: real Alumni Portal

`portal.html` is a placeholder. For actual member accounts (login, meeting minutes, financials, archives), you'll need a backend — GitHub Pages alone can't do auth. Recommended path: Supabase (free tier) for auth + a members-only database, layered onto this same static site. Ask Claude to help wire this up when you're ready.

## Adding blog posts (blog.html)

Posts live directly in `blog.html`, newest at the top. Add a new one like this:

```html
<article class="post-card">
  <p class="post-date">Month Year</p>
  <h2>Post Title</h2>
  <div class="post-body">
    <p>Your text here.</p>
  </div>
</article>
```
