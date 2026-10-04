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

### Add a certification — easiest way (GitHub website, zero code)
1. Open the repo on github.com → click the **`certs`** folder →
   **Add file → Upload files** → drag your cert in (PNG/JPG/PDF) → **Commit changes**.
2. Done. The card appears on the site automatically within a minute —
   the title comes from the filename (`oswe-cert.png` → "oswe cert").

The page reads the `certs/` folder through GitHub's public API, so this
works with no local setup at all. (Hard-refresh the page if you just uploaded.)

Each card gets a **category chip** detected from the filename — name your
file with a keyword and it colors itself: `web`, `api`, `network`, `forensic`,
`stego`, `pentest`, `osint` (e.g. `API-RTA.pdf` → "api security" chip).

### PDF preview thumbnail
If a PDF needs a preview image on its card, put one in `certs/previews/`
with the **same base name** (`API-RTA.pdf` → `certs/previews/API-RTA.png`,
`.jpg`, or `.webp`). The card shows it as a thumbnail; without one it shows
the category illustration instead. Generate one locally with:

```bash
pdftoppm -singlefile -jpeg -r 110 certs/API-RTA.pdf certs/previews/API-RTA
# then shrink it (a 900px-wide card is plenty):
convert certs/previews/API-RTA.jpg -resize 900x -quality 82 certs/previews/API-RTA.jpg
```

(or just ask Claude to generate the preview for you.)

### ...or hand-write the card (full control over title / issuer / verify link)
In `index.html`, in the `certs` section, replace one of the placeholder
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

### Add a skill / service / timeline entry / project card
- Skill: add a `<span class="tag">...</span>` inside any `.tags` group.
- Service: copy a `.card` block in the `services` section.
- Timeline: copy a `.t-item` block in the `journey` section.
- Writeup card: copy any `.card` in the `writeups` grid.
- Most cards and entries have a commented example right next to them.

### HackMD writeups
The "HackMD — lab writeups" block mirrors your notes from
[hackmd.io/@sh1n0b1Xby73](https://hackmd.io/@sh1n0b1Xby73). It's a static list,
so when you publish a new note there, either copy a card in `index.html` and
link the new note, or ask Claude to re-sync the profile for you.

### Contact form & email
The form opens the visitor's mail app with the message pre-filled and sends
to `ny1m1nh737@gmail.com`. If you change your address later, it appears in
`index.html` in three places: the hero mail icon, the contact links, and the
`TO` variable at the top of the contact-form script.

### Theme tweaks
Colors and fonts are CSS variables at the top of `style.css` — change
`--accent`, `--bg`, `--mono`, etc. there. The ☀/☾ button in the navbar
switches to the light theme (defined in the `body.light` block, right below
the dark variables); the visitor's choice is remembered in their browser.

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
