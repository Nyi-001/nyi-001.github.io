# sh1n0b1Xby73 — portfolio

My cybersecurity portfolio, live at **[nyi-001.github.io](https://nyi-001.github.io)**.

Clean modern static site — plain HTML/CSS, no build step, dark/light theme,
mobile responsive. Everything is hosted straight from this repo by GitHub Pages
(branch: `main`, root folder).

## Structure

```
.
├── index.html          # the portfolio (edit this)
├── style.css           # terminal/CRT theme
├── blog/               # blog posts — one HTML file per post
└── certs/              # certification images
```

## How to update

### Add a certification
1. Put the image in `certs/` (e.g. `certs/oswe.png`)
2. In `index.html`, in the `certs` section, replace one of the placeholder
   `.box` cards with the example card that's commented out above them:
   ```html
   <div class="box">
     <div class="cert-img"><img src="certs/oswe.png" alt="OSWE certificate"></div>
     <h3>Offensive Security Web Expert</h3>
     <p>Advanced web app attacks and exploitation.</p>
     <div class="cert-issuer">OffSec · 2026 · <a href="#">verify</a></div>
   </div>
   ```
   (The card can be a PDF link too: swap `<img src="...">` for
   `<a href="certs/my-cert.pdf">view PDF</a>` — style it however you like.)

### Publish a blog post
1. Copy the template: `cp blog/hello-world.html blog/my-post.html`
2. Edit title, date, and body
3. Add a card to the `blog` section in `index.html` (there's a commented
   example right below the first post)

### Add a project / writeup / skill / timeline entry
Copy any `.box` card in the `projects` or `writeups` section of `index.html`
(and any `.skill` bar or `.t-item` timeline entry), then change the title,
description, chips and link. Skill bars take a `data-width="85"` percentage.

## Publishing workflow

```bash
git add .
git commit -m "update: ..."
git push
```

GitHub Pages rebuilds automatically — the site is live ~1 minute after push.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```
