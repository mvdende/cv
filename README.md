# Online CV — Micha van der Ende

A single-page, self-contained CV site. No build step, no dependencies, no framework —
just `index.html` and a portrait image.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole site: content, styling and the one line of JavaScript behind the print button |
| `portrait.jpg` | Header photo (extracted from the original CV) |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is instead of running Jekyll |

## Before you publish — one thing to fix

Open `index.html` and replace both occurrences of `YOUR-LINKEDIN-HANDLE`
with your real LinkedIn handle (the part after `linkedin.com/in/`):

```
https://www.linkedin.com/in/YOUR-LINKEDIN-HANDLE
```

## Publishing to GitHub Pages

### Option A — a personal site at `https://<username>.github.io`

1. On GitHub, create a **public** repository named exactly `<your-username>.github.io`
   (for example `michavanderende.github.io`). Don't add a README during creation.
2. Upload `index.html`, `portrait.jpg` and `.nojekyll` to the root of the repo —
   either via **Add file → Upload files** in the browser, or with git:

   ```bash
   git init
   git add .
   git commit -m "Add online CV"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
   git push -u origin main
   ```
3. Go to **Settings → Pages**. Under *Build and deployment*, set
   **Source: Deploy from a branch**, **Branch: `main`**, **Folder: `/ (root)`**, then **Save**.
4. Wait a minute, then open `https://<your-username>.github.io`.

### Option B — a project site at `https://<username>.github.io/cv`

Same as above, but name the repository `cv` (or anything you like). The site
will live at `https://<username>.github.io/cv/`. Everything here uses relative
paths, so it works from a subfolder without changes.

### Custom domain (optional)

In **Settings → Pages → Custom domain**, enter your domain and follow the DNS
instructions GitHub shows. Tick **Enforce HTTPS** once the certificate is issued.

## Editing later

Everything lives in `index.html` and is plain HTML, in the order it appears on the page:

- **Header** — name, role, location, LinkedIn (`<header class="masthead">`)
- **Profile** — the intro paragraphs and the four "at a glance" numbers
- **Focus areas** — the tag list; add or remove `<li>` items
- **Experience** — each role is one `<article class="job">`. Older roles sit inside
  the `<details class="earlier">` block, which is collapsed by default. To promote a
  role, move its `<article>` out of that block.
- **Skills** — proficiency is drawn with filled `●` and greyed `<i>●</i>` dots.
  Four dots total per row; keep the `aria-label` in sync for screen readers.
- **Education & certification**, then **Beyond work**.

Colours, spacing and fonts are the CSS custom properties at the top of the
`<style>` block (`--accent`, `--ink`, `--maxw`, and so on) — change one value
and it applies throughout.

## Notes

- The page is responsive down to phone width and has a dedicated print stylesheet:
  the **Print / save as PDF** button produces a clean document with all the earlier
  assignments expanded and the button itself hidden.
- No date of birth, phone number or home address is included, since the page is public.
- No external requests are made — no fonts, analytics or CDN scripts — so the page
  loads instantly and adds no cookies or trackers.
