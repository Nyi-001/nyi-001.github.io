# sh1n0b1Xby73 — portfolio

My cybersecurity portfolio, live at **[nyi-001.github.io](https://nyi-001.github.io)**.

Handcrafted security-themed static site — plain HTML/CSS + a few lines of vanilla JS.
No frameworks, no build step, one font request, mobile responsive, dark by design.
Everything is hosted straight from this repo by GitHub Pages (branch: `main`, root folder).

## Structure

```
.
├── index.html          # the single-page portfolio (edit this)
├── style.css           # theme — colors & fonts live in :root at the top
├── blog/               # blog posts / writeups — one HTML file per post
└── certs/              # certification images
```

## How to update

### Add a certification
1. Put the image in `certs/` (e.g. `certs/oswe.png`)
2. In `index.html`, in the `certs` section, replace one of the placeholder
   cards with the example card that's commented out above them:
   ```html
   <div class="card">
     <div class="cert-img"><img src="certs/oswe.png" alt="OSWE certificate" loading="lazy"></div>
     <h3>Offensive Security Web Expert</h3>
     <p>Advanced web application attacks and exploitation.</p>
     <div class="card-meta"><span>OffSec · 2026</span><a class="read-more" href="#">verify ↗</a></div>
   </div>
   ```

### Publish a writeup / blog post
1. Copy the template: `cp blog/hello-world.html blog/my-post.html`
2. Edit title, date, and body
3. Add a card to the `writeups` section in `index.html`
   (there's a commented example at the bottom of the post grid)

### Add a skill / timeline entry / project card
- Skill: add a `<span class="tag">...</span>` inside any `.tags` group.
- Timeline: copy a `.t-item` block in the `journey` section.
- Writeup card: copy any `.card` in the `writeups` grid.
- Most cards and entries have a commented example right next to them.

### Receive contact-form messages
The form opens the visitor's mail app. Change `you@example.com` to your real
address — it appears in `index.html` in three places: the hero mail icon,
the contact links, and the `TO` variable at the top of the contact-form script.

### Theme tweaks
Colors and fonts are CSS variables at the top of `style.css` — change
`--accent`, `--bg`, `--mono`, etc. there.

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
