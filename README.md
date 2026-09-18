# Rachel Leslie — Link Site

Static link-in-bio page for Rachel Leslie.

**Stack:** Single `index.html` + Tailwind via CDN-style classes. Zero build step. Pure HTML/CSS/JS — opens in any browser, deploys to any static host.

## Local preview

```bash
python3 -m http.server 8765
# open http://localhost:8765/
```

## File map

```
rachelleslie-site/
├── index.html                  # the whole site
├── assets/
│   ├── logos/                  # official platform logos (Fanvue, IG, Bluesky)
│   │   ├── fanvue-256.png      # official Fanvue "F" mark, green
│   │   ├── instagram-256.png   # official Instagram camera icon
│   │   ├── bsky-256.png        # official Bluesky butterfly
│   │   └── fanvue.png          # smaller Fanvue favicon variant
│   └── photos/                 # drop your photos here
│       ├── bg.jpg              # hero background (blurred behind the page)
│       ├── avatar.jpg          # profile pic in the gradient ring
│       ├── grid-1.jpg          # photo grid cell 1
│       ├── grid-2.jpg          # photo grid cell 2
│       ├── grid-3.jpg          # photo grid cell 3
│       ├── grid-4.jpg          # photo grid cell 4
│       ├── grid-5.jpg          # photo grid cell 5
│       └── grid-6.jpg          # photo grid cell 6
└── README.md                   # this file
```

The page loads each photo with a JS `tryLoad()` — missing files just leave a styled dark cell, so the site never breaks if a photo isn't in place.

## How to add photos

1. Drop JPGs into `assets/photos/` using the filenames above
2. Recommended sizes:
   - `bg.jpg` — 1920x1080 or larger (gets blurred, so detail is fine)
   - `avatar.jpg` — square, 800x800 minimum
   - `grid-N.jpg` — square, 800x800 minimum
3. Refresh the browser — the page auto-detects the files

If you add more than 6 grid photos, add `<div class="cell" id="cell6"></div>` (and 7, 8...) in the `.photo-grid` block and add the matching filenames in the `photos.grid` array at the bottom of the script.

## Deploy to GitHub Pages

1. Create a repo on Rachel's GitHub account named `therachelleslie`
2. Push this folder:

```bash
cd ~/Documents/Hermes/rachelleslie-site
git add -A
git commit -m "Initial: Rachel Leslie link site"
git branch -M main
git remote add origin https://github.com/<rachel-username>/therachelleslie.git
git push -u origin main
```

3. On GitHub: Settings → Pages → Source: `main` branch, `/ (root)` folder
4. The site will be live at `https://<rachel-username>.github.io/therachelleslie/`
5. In Settings → Pages → Custom domain, point it at whatever Rachel owns (e.g. `rachelleslie.com`)

## Editing the page

Open `index.html` in any editor. Top of the file has all the colors and typography as CSS variables — change them there once and the whole page updates.

Common edits:

- **Bio text**: search for `Official links. New posts every week.` in the hero section
- **Stats numbers**: search for `120+`, `14.2K`, `3`
- **Footer email**: search for `contact@rachelleslie.com`
- **Accent colors**: edit `--accent-1`, `--accent-2`, `--accent-3` in `:root`
