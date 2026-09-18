# Rachel Leslie — Link Site

A simple link-in-bio page. One photo as a blurred background, a glassmorphic card with the link buttons centered on top. Below the fold, photos stack vertically as you scroll.

**Stack:** Single `index.html` + custom CSS. Zero build step. Pure HTML/CSS/JS — opens in any browser, deploys to any static host.

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
│   ├── logos/                  # official platform logos
│   │   ├── fanvue-256.png      # official Fanvue "F" mark, green
│   │   ├── instagram-256.png   # official Instagram camera icon
│   │   ├── bsky-256.png        # official Bluesky butterfly
│   │   └── fanvue.png          # smaller Fanvue favicon variant
│   └── photos/                 # drop your photos here
│       ├── bg.jpg              # background photo (blurred behind the card)
│       ├── avatar.jpg          # profile pic in the gradient ring
│       ├── photo-1.jpg         # gallery photo 1
│       ├── photo-2.jpg         # gallery photo 2
│       ├── photo-3.jpg         # gallery photo 3
│       ├── ...
│       └── photo-10.jpg        # gallery photo 10
└── README.md
```

## How it works

**Background.** A single photo (`bg.jpg`) is fixed to the viewport and blurred slightly. The links card sits centered on top of it.

**Card.** Glassmorphic, centered, holds the avatar, name, handle, bio, stats, and three link buttons (Fanvue, Instagram, Bluesky). Stays put while you scroll past it.

**Gallery.** Below the card section, photos stack one after another. Each one renders at its **natural aspect ratio** — landscape photos stay landscape, portrait photos stay portrait. No cropping, no forced aspect.

## How to add photos

Drop JPGs into `assets/photos/` using these filenames:

- `bg.jpg` — the blurred background. Recommended 1920px wide, ~500KB.
- `avatar.jpg` — the circular profile picture. Square, 800x800 minimum.
- `photo-1.jpg` through `photo-N.jpg` — the gallery. Any aspect ratio.

**To add more gallery photos**, just add `<div class="photo" data-n="11"></div>` (and 12, 13, ...) to the `.photo-stack` block in `index.html`. The JS picks up anything with a `data-n` attribute.

The page uses graceful fallback — missing photos just leave styled dark placeholders.

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

- **Bio text**: search for `Official links. New posts every week.`
- **Stats numbers**: search for `120+`, `14.2K`, `3`
- **Footer text**: search for `All rights reserved`
- **Accent colors**: edit `--accent-1`, `--accent-2`, `--accent-3` in `:root`
- **Background blur amount**: edit `filter: blur(18px)` in the `.bg .img` rule
- **Background overlay darkness**: edit the gradient stops in `.bg::after`
