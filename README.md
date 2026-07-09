# Overknight Website — Setup Guide

## 1. Upload the files to GitHub

In your `LeslyLeonDev` repo (the one currently holding `index.html` and `app-ads.txt`):

1. Click **Add file → Upload files**.
2. Drag in every file/folder from this package: all the `.html` files, plus the `css/`, `js/`, and `assets/` folders, plus `robots.txt` and `sitemap.xml`.
3. GitHub preserves folder structure automatically when you drag a folder in — you don't need to recreate folders manually.
4. Commit directly to `main`.
5. Your existing `index.html` and `app-ads.txt` are fine to keep — the new `index.html` in this package will simply replace the old one.

## 2. Adding images so they show on the site

Every image on the site right now is a placeholder panel labeled with what should go there (e.g. "Hero Render — Overknight Promotional Art"). To swap in real art:

1. **Pick the right folder:**
   - Game screenshots, artwork, hero renders → `assets/img/`
   - Your site icon / favicon → `assets/icons/icon.png`

2. **Upload images to that folder on GitHub:**
   - Open the `assets/img` folder in your repo.
   - Click **Add file → Upload files**, drag your `.jpg`/`.png` files in, commit.
   - Keep file sizes reasonable (compress large screenshots — under ~500KB each is a good target) so the site loads fast.

3. **Reference the image in the HTML.** Find the placeholder `<div class="art-block">...</div>` you want to replace and swap it for an `<img>` tag, for example:

   ```html
   <!-- Before -->
   <div class="art-block" style="aspect-ratio:21/9;">Hero Render — Overknight Promotional Art</div>

   <!-- After -->
   <img src="assets/img/hero-render.jpg" alt="Overknight hero artwork" style="width:100%; aspect-ratio:21/9; object-fit:cover; border:1px solid var(--line-dim);">
   ```

   The path `assets/img/hero-render.jpg` is **relative to the HTML file** — since every page sits in the repo root and `assets/img` sits right next to it, this same relative path works from every page.

4. **Your site icon:** upload your icon file as `assets/icons/icon.png`. Every page already links to it via `<link rel="icon" ... href="assets/icons/icon.png">`, so it'll just start working once the file exists at that path — no HTML changes needed.

5. **The Open Graph / social preview image** (`assets/img/og-cover.jpg`, referenced in each page's `<meta property="og:image">`) is what shows up when the link is shared on Discord, Twitter, etc. Upload a 1200×630px image there for best results.

## 3. Enabling GitHub Pages (if not already on)

1. Go to your repo's **Settings → Pages**.
2. Under **Build and deployment**, set Source to **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`.
4. Save. Your site will be live at `https://leslyleondev.github.io/<repo-name>/` within a minute or two.

> Note: the canonical URLs and sitemap.xml in this package assume the site lives at `https://gamewavestudios.github.io/`. If your actual GitHub Pages URL is different (e.g. it includes a repo name path, or uses your `LeslyLeonDev` username), search-and-replace that domain across the HTML files and `sitemap.xml`/`robots.txt` to match.

## 4. Page list

| Page | File |
|---|---|
| Home | `index.html` |
| Download | `download.html` |
| Game Modes (ThunderRush / VelocityVentures) | `game-modes.html` |
| Media (videos + gallery) | `media.html` |
| Development Timeline | `development.html` |
| News | `news.html` |
| Wiki | `wiki.html` |
| GameWaveStudios (about) | `studio.html` |
| Contact | `contact.html` |
| Privacy Policy | `privacy.html` |
| Terms of Service | `terms.html` |

All pages share `css/main.css` and `js/main.js`, so a style change in one place updates the whole site.
