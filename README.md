# Rachel Leslie — Link Site

Wedding-style link-in-bio page for Rachel Leslie. Two photos cross-fade as you scroll, with a glassmorphic links card hovering centered the whole time.

**Stack:** Single `index.html` + custom CSS (no Tailwind). Zero build step. Pure HTML/CSS/JS — opens in any browser, deploys to any static host.

## Local preview

```bash
python3 -m http.server 8765
# open http://localhost:8765/
```

## How the scroll-driven cross-fade works

The page is 3 viewports tall (the "stage"). Two photo layers stack on top of each other inside a `position: fixed` background container. As you scroll through the stage:

- **0% to 33%** — Photo A is fully visible
- **33% to 66%** — Photo A fades out, Photo B fades in
- **66% to 100%** — Photo B is fully visible
- **85% onward** — the floating card fades out so the gallery appears cleanly below

The links card itself is `position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%)` — so it hovers in the center of the viewport the entire time, like a wedding-site intro.

Three pips on the right edge light up to show which photo you're currently on.

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
│       ├── bg.jpg              # Photo A — first background photo
│       ├── bg-2.jpg            # Photo B — second photo, cross-fades in
│       ├── avatar.jpg          # profile pic in the gradient ring
│       ├── photo-1.jpg         # gallery card 1
│       ├── photo-2.jpg         # gallery card 2
│       ├── photo-3.jpg         # gallery card 3
│       ├── photo-4.jpg         # gallery card 4
│       ├── photo-5.jpg         # gallery card 5
│       ├── photo-6.jpg         # gallery card 6
│       ├── photo-7.jpg         # gallery card 7
│       └── photo-8.jpg         # gallery card 8
└── README.md
```

## How to add more photos

**Hero cross-fade photos** — drop two JPGs named `bg.jpg` and `bg-2.jpg`. They cross-fade on scroll. To add a third photo, copy the existing photo-layer div in `index.html` and adjust the JS in the `<script>` block.

**Gallery cards** — drop JPGs as `photo-1.jpg` through `photo-N.jpg`. To add more, add a matching `<div class="photo-card" data-n="N">` to the `.photo-stack` block and extend the `Array.from({length: N})` in the script.

Recommended sizes:
- Hero photos: 1920px wide, optimized JPGs (300-700KB each)
- Avatar: square, 800x800 minimum
- Gallery cards: square or 4:5 portrait, 800px wide minimum

The page uses a `tryLoad()` helper so missing files leave styled dark placeholders rather than breaking.

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
- **Footer**: search for `Back to top` or `Rachel Leslie. All rights reserved.`
- **Accent colors**: edit `--accent-1`, `--accent-2`, `--accent-3` in `:root`
- **Cross-fade timing**: search for `1 - t * 2` and `(t - 0.33) / 0.33` in the JS section
