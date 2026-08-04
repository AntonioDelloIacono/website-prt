# How to update and publish this website

This site is three files (plus a folder of images). You never need to install
anything or write code to make everyday changes. This guide assumes zero
web experience.

```
prtc-website/
├── index.html        ← all the text on the site lives here
├── privacy.html       ← standalone privacy page (only reachable via the
│                          "Privacy" button at the bottom of the site —
│                          not listed in the main menu). Edit it the same
│                          way as index.html.
├── style.css          ← colours, fonts, layout (you shouldn't need this)
├── CNAME               ← tells GitHub which domain to serve (leave alone)
├── HOW-TO-UPDATE.md   ← this guide
└── images/
    ├── logo.png              ← dark logo (transparent background), used in the header
    ├── logo-white.png        ← white logo (transparent background), used in the dark footer
    ├── framework-figure.png  ← Figure 1 from the founding pre-print, shown in "The framework" section
    ├── favicon-32.png        ← small browser-tab icon
    └── favicon-512.png       ← larger app icon
```

---

## 1. Editing text

Open `index.html` in any plain text editor (Notepad, TextEdit, or — nicer —
the free app [VS Code](https://code.visualstudio.com/)). **Do not use Microsoft
Word or Google Docs to edit it**, as they will corrupt the file.

The file is broken into clearly labelled blocks like this:

```html
<!-- ===================================================================
     HERO
     EDIT: headline, subheading, and the two button labels/links below.
     =================================================================== -->
```

Find the section you want to change using these comments (or your editor's
search, `Ctrl+F` / `Cmd+F`), then only change the plain text sitting
**between** the `<tags>` — never delete a `<...>` or `</...>` tag itself.

**Example.** To change the headline, find this line:

```html
<h1>From variability to precision in resistance training.</h1>
```

and simply retype the sentence between `<h1>` and `</h1>`.

A few symbols you'll see and can safely leave alone:
- `&mdash;` is a long dash (—), `&rsquo;` is a curly apostrophe (’), `&amp;` is "&". These exist because a few characters aren't allowed to appear directly in HTML text — just leave them as they are, or copy an existing one if you need the same symbol elsewhere.

Save the file when you're done, using **UTF-8** encoding if your editor asks
(this is the default in VS Code and Notepad).

## 2. Adding or removing a card, member, or education entry

Sections like "Focus areas" and "Education" are made of repeated
`<div class="card">...</div>` blocks. To add one, copy an existing whole
block, paste it directly above the closing `</div>` of that section, and
edit the text inside your new copy. To remove one, delete the whole block
from its opening tag to its matching closing tag.

**Members** work the same way but with `<details class="member-item">...
</details>` blocks instead — each one is a name that expands when clicked to
show a photo and bio. Copy a whole block to add a member, delete one to
remove a member. To use a real photo, add the image file to the `images`
folder and change that member's `src="images/avatar-placeholder.png"` to
your new filename (both the small thumbnail and the larger photo — a
square image works best for both).

## 3. Changing the contact email

Search the file for `contact@example.org` (it appears twice — once in the
"Get involved" button, once in the footer) and replace both with your real
address.

## 4. Replacing the logo

Drop a new file into the `images` folder and update the `src="images/..."`
reference in `index.html` to match its filename. Keep a roughly similar
width-to-height ratio so it doesn't look stretched. If you change the logo,
you'll also want a plain-white version of it for the dark footer — ask
Claude (or any designer) to make one for you if needed.

## 5. Publishing the site (and future updates)

The easiest way to get this online with **no coding and no cost**:

### Option A — Netlify Drop (fastest, good for occasional updates)
1. Go to **[app.netlify.com/drop](https://app.netlify.com/drop)**.
2. Drag the whole `prtc-website` folder onto the page.
3. Netlify gives you a live web address immediately.
4. To update the site later: make your edits, then drag the folder onto
   the same Netlify page again (or onto your site's "Deploys" tab) to
   replace it. It takes about 10 seconds.
5. Optional: in Netlify's site settings you can connect your own domain
   name (e.g. `prtconsortium.org`) instead of the free `*.netlify.app` one.

### Option B — GitHub Pages (best if several people will edit the site)
1. Create a free account at [github.com](https://github.com).
2. Create a new repository and upload these files (there's an "Upload
   files" button in the browser — no command line needed).
3. In the repository's Settings → Pages, set it to publish from the
   main branch.
4. From then on, anyone with access can click a file (e.g. `index.html`),
   press the pencil/edit icon, change the text in the browser, and click
   "Commit changes" — the live site updates automatically within a minute.

Either option is free, requires no server, and needs no ongoing
maintenance beyond editing text when something changes.

## 6. If something looks broken

The most common cause is a missing or mismatched `<` `>` tag, or a stray
quotation mark. If a change breaks the layout, undo your last edit (or
compare against a saved backup copy of `index.html`) and try again more
narrowly — change one sentence at a time and check the result before
moving to the next.

## 7. Getting further help

You can always paste your `index.html` file into an AI assistant (like
Claude) and ask it to make a specific change for you in plain English —
e.g. "add a fifth founding member card with this name and affiliation."
That's usually faster than editing HTML by hand.
