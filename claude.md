# Humza's DEN — Project Brief

## What is this?

**Humza's DEN** — Daily Engineering Notebook.
A minimal personal site / engineering logbook for Humza Khatri. The goal is a living public notebook where Humza writes about what he's building, learning, and figuring out. No polish required. Rough is fine.

Live at: **humzakhatri.com**
Repo: **https://github.com/humzakhatri/Humza-den**

---

## Stack

- **Astro v6** — static output
- **Plain Markdown** — all content lives in `src/content/den/` as `.md` files
- **GitHub Pages** — hosting, deployed via GitHub Actions on push to `main`
- **No framework** — vanilla Astro, no React, no Tailwind
- **Zero cost** — everything is free

---

## Design

### Vibe
Minimal, not heavy on the eyes. Engineering logbook aesthetic. Clean and readable. Think personal notebook, not agency site.

### Fonts
**IBM Plex Sans** — body and UI  
**IBM Plex Mono** — dates, labels, tags, meta text, code  
Both loaded from Google Fonts. The full IBM Plex family — cohesive, technical but warm.

### Colors (CSS variables)
```css
--color-peach:        #FDDCB5;   /* used for h2 highlights in prose */
--color-teal:         #B2DDD4;   /* primary accent background (buttons etc) */
--color-yellow:       #FAF0A0;   /* tags */
--color-blue:         #BDD7F0;   /* available for use */

--color-bg:           #FAFAF8;
--color-surface:      #FFFFFF;
--color-border:       #E8E6E1;
--color-text:         #2C2C2C;
--color-text-muted:   #888580;
--color-text-light:   #B0ADA8;

--color-accent:       #5BADA0;   /* teal, used for links and hover states */
--color-accent-soft:  var(--color-teal);
```

### Layout
- Max width: `860px`, centered
- Clean header: site title left, nav right
- Footer: minimal, just name + GitHub link
- Responsive — single column on mobile

---

## Pages

### `/` — Homepage
- Short intro about Humza: love for building, tech, software
- List of 5 most recent DEN entries (title + date)
- Two CTA buttons: "What I'm up to now →" and "GitHub"

### `/now` — The main DEN page
- Shows the **latest** DEN entry as the main content
- **Sidebar** on the right: archive grouped by month, links to all past entries
- This is the heart of the site

### `/den/[slug]` — Individual entry
- Full entry content
- Back link to `/now`
- Date + tags displayed in header

### `/contact` — Contact page
- Simple form: Name, Email, Message
- Form posts to **Formspree** — action URL is `https://formspree.io/f/YOUR_FORM_ID`
- **TODO: Replace `YOUR_FORM_ID`** with the real Formspree form ID
- Direct email also shown (update the placeholder email to Humza's real one)

---

## Content

DEN entries live in `src/content/den/` as Markdown files.

### Frontmatter schema
```yaml
---
title: "Entry title"
date: 2026-05-31
tags: ["tag1", "tag2"]   # optional
draft: false              # optional, defaults to false
---
```

### File naming convention
`YYYY-MM-DD.md` — one entry per day, named by date.

---

## Project Structure

```
src/
  content/
    den/               ← DEN entries go here as .md files
  content.config.ts    ← Astro v6 content collection config
  layouts/
    BaseLayout.astro   ← shared layout, header, footer, global styles
  pages/
    index.astro        ← homepage
    now.astro          ← now page with sidebar
    contact.astro      ← contact form
    den/
      [slug].astro     ← individual entry page
  styles/
    global.css         ← all global styles, CSS variables, fonts
.github/
  workflows/
    deploy.yml         ← build + deploy to GitHub Pages on push to main
public/
  CNAME                ← humzakhatri.com
```

---

## GitHub Actions Deploy

On every push to `main`:
1. Install dependencies (`npm ci`)
2. Build (`npm run build`) → outputs to `dist/`
3. Deploy `dist/` to GitHub Pages

GitHub repo Settings → Pages → Source must be set to **GitHub Actions**.

---

## Pending / TODO

- [ ] Replace `YOUR_FORM_ID` in `src/pages/contact.astro` with real Formspree ID
- [ ] Update placeholder email on contact page to Humza's real email
- [ ] Write real homepage intro copy (current copy is placeholder)
- [ ] Write first real DEN entry (replace sample `2026-05-31.md`)
- [ ] Add categorization/tagging UI to entries (deferred, ship later)
- [ ] Projects page (deferred, ship later)
