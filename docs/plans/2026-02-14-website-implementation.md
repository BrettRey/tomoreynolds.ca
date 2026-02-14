# Tomo Reynolds Website Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a booking-focused single-page musician website for Tomo Reynolds at tomoreynolds.ca.

**Architecture:** Plain HTML/CSS static site (no JS, no build tools). Single-page scroll with anchored sections: hero, about, media, contact, footer. Hosted on GitHub Pages. Design inherits brettreynolds.ca typography (EB Garamond) with a dark jazz-club palette. All colours in CSS custom properties for easy restyling.

**Tech Stack:** HTML5, CSS3, Google Fonts (EB Garamond), Formspree (contact form), GitHub Pages hosting.

**Design doc:** `docs/plans/2026-02-14-website-design.md`

**Reference site:** `/Users/brettreynolds/Documents/LLM-CLI-projects/personal/personal-website/` (brettreynolds.ca source)

---

### Task 1: Initialize git repo and rename photo

**Files:**
- Rename: `1769986865510.jpg` -> `tomo.jpg`

**Step 1: Initialize git repo**

```bash
cd /Users/brettreynolds/Documents/LLM-CLI-projects/personal/tomo-website
git init
```

**Step 2: Rename the photo**

```bash
mv 1769986865510.jpg tomo.jpg
```

**Step 3: Commit initial state**

```bash
git add README.md tomo.jpg docs/
git commit -m "Initial commit: README, photo, design docs"
```

---

### Task 2: Create style.css

**Files:**
- Create: `style.css`

The CSS defines the full visual language. Key differences from brettreynolds.ca:
- Dark background (#1a1a1a) instead of light (#fafafa)
- Warm off-white text (#f0ead6) instead of dark (#222)
- Amber accent (#c45a3c) instead of maroon (#800020)
- All colours as CSS custom properties (`:root` block)
- Hero section: full-width with centred content
- Sections separated by subtle dividers
- CTA button styled for the accent colour
- Contact form styling
- Responsive at 600px breakpoint (matching brettreynolds.ca)

**Step 1: Write style.css**

```css
/* Tomo Reynolds - Jazz Pianist Website
   Typography: EB Garamond (body), Georgia fallback
   Palette: dark background, warm off-white text, amber accent
   All colours in custom properties for easy restyling.
*/

@import url('https://fonts.googleapis.com/css2?family=EB+Garamond:ital,wght@0,400;0,500;0,600;1,400;1,500&display=swap');

:root {
  --bg: #1a1a1a;
  --text: #f0ead6;
  --text-muted: #a89f91;
  --accent: #c45a3c;
  --accent-hover: #d4795f;
  --divider: #333;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  font-size: 18px;
  line-height: 1.6;
  scroll-behavior: smooth;
}

body {
  font-family: 'EB Garamond', Georgia, 'Times New Roman', serif;
  color: var(--text);
  background-color: var(--bg);
  padding: 2rem 1rem;
  max-width: 800px;
  margin: 0 auto;
}

/* Headings */
h1 {
  font-size: 2.2rem;
  font-weight: 400;
  font-variant: small-caps;
  letter-spacing: 0.1em;
  margin-bottom: 0.25rem;
}

h2 {
  font-size: 1.3rem;
  font-weight: 400;
  font-variant: small-caps;
  letter-spacing: 0.05em;
  margin-bottom: 1rem;
  border-bottom: 1px solid var(--divider);
  padding-bottom: 0.25rem;
}

/* Links */
a {
  color: var(--accent);
  text-decoration: none;
}

a:hover {
  color: var(--accent-hover);
  text-decoration: underline;
}

/* Divider */
hr {
  border: none;
  border-top: 1px solid var(--divider);
  margin: 2.5rem 0;
}

/* Hero section */
.hero {
  text-align: center;
  margin-bottom: 1rem;
}

.hero-photo {
  width: 240px;
  height: auto;
  border-radius: 4px;
  margin-bottom: 1rem;
}

.tagline {
  font-size: 1.1rem;
  color: var(--text-muted);
  letter-spacing: 0.05em;
  margin-bottom: 1.5rem;
}

.cta {
  display: inline-block;
  font-family: 'EB Garamond', Georgia, serif;
  font-size: 1rem;
  color: var(--text);
  background: var(--accent);
  padding: 0.5rem 1.5rem;
  border-radius: 3px;
  text-decoration: none;
  letter-spacing: 0.03em;
}

.cta:hover {
  background: var(--accent-hover);
  text-decoration: none;
  color: var(--text);
}

/* About section */
.about p {
  font-size: 1rem;
  line-height: 1.7;
  margin-bottom: 1rem;
}

/* Media section */
.video-embed {
  position: relative;
  padding-bottom: 56.25%; /* 16:9 */
  height: 0;
  overflow: hidden;
  margin-bottom: 1rem;
}

.video-embed iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: none;
}

.media-links {
  list-style: none;
  margin-top: 1rem;
}

.media-links li {
  margin-bottom: 0.5rem;
}

/* Contact section */
.contact-form {
  max-width: 500px;
}

.contact-form label {
  display: block;
  font-size: 0.95rem;
  color: var(--text-muted);
  margin-bottom: 0.25rem;
  margin-top: 1rem;
}

.contact-form input,
.contact-form textarea,
.contact-form select {
  width: 100%;
  font-family: 'EB Garamond', Georgia, serif;
  font-size: 1rem;
  color: var(--text);
  background: #252525;
  border: 1px solid var(--divider);
  border-radius: 3px;
  padding: 0.5rem;
}

.contact-form input:focus,
.contact-form textarea:focus,
.contact-form select:focus {
  outline: none;
  border-color: var(--accent);
}

.contact-form textarea {
  height: 8rem;
  resize: vertical;
}

.contact-form button {
  display: inline-block;
  font-family: 'EB Garamond', Georgia, serif;
  font-size: 1rem;
  color: var(--text);
  background: var(--accent);
  border: none;
  border-radius: 3px;
  padding: 0.5rem 1.5rem;
  margin-top: 1rem;
  cursor: pointer;
  letter-spacing: 0.03em;
}

.contact-form button:hover {
  background: var(--accent-hover);
}

.contact-fallback {
  margin-top: 1rem;
  font-size: 0.95rem;
  color: var(--text-muted);
}

/* Footer */
footer {
  margin-top: 3rem;
  text-align: center;
  font-size: 0.85rem;
  color: var(--text-muted);
}

.social-links {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 0.5rem 1.5rem;
  margin-bottom: 1rem;
  font-size: 0.95rem;
}

/* Responsive */
@media (max-width: 600px) {
  html {
    font-size: 16px;
  }

  .hero-photo {
    width: 180px;
  }

  .contact-form {
    max-width: 100%;
  }
}
```

**Step 2: Commit**

```bash
git add style.css
git commit -m "Add stylesheet: dark jazz palette, CSS custom properties"
```

---

### Task 3: Create index.html

**Files:**
- Create: `index.html`

This is the single-page site with all sections. Includes Schema.org JSON-LD and Open Graph meta tags. The Formspree form action URL will need to be updated once a Formspree account is created (use placeholder `https://formspree.io/f/FORM_ID` for now).

**Step 1: Write index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Tomo Reynolds - Jazz pianist based in Toronto. Available for jazz engagements, private events, and corporate functions.">

  <!-- Open Graph -->
  <meta property="og:title" content="Tomo Reynolds - Jazz Pianist">
  <meta property="og:description" content="Jazz pianist based in Toronto. Available for engagements, private events, and corporate functions.">
  <meta property="og:type" content="profile">
  <meta property="og:url" content="https://tomoreynolds.ca/">
  <meta property="og:image" content="https://tomoreynolds.ca/tomo.jpg">

  <title>Tomo Reynolds - Jazz Pianist</title>
  <link rel="stylesheet" href="style.css">

  <!-- Schema.org structured data -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "Person",
    "name": "Tomo Reynolds",
    "url": "https://tomoreynolds.ca",
    "jobTitle": "Jazz Pianist",
    "knowsAbout": ["Jazz", "Piano", "Music Performance"],
    "alumniOf": {
      "@type": "CollegeOrUniversity",
      "name": "Humber Polytechnic"
    },
    "sameAs": [
      "https://ca.linkedin.com/in/tomo-reynolds-07992918a",
      "https://www.youtube.com/@towmoe",
      "https://musescore.com/user/25260836",
      "https://ca.pinterest.com/tomoreyn/",
      "https://www.reddit.com/user/tomoreyn/"
    ]
  }
  </script>
</head>
<body>

  <!-- Hero -->
  <section class="hero">
    <img class="hero-photo" src="tomo.jpg" alt="Tomo Reynolds playing piano">
    <h1>Tomo Reynolds</h1>
    <p class="tagline">Jazz pianist · Toronto</p>
    <a class="cta" href="#contact">Book me</a>
  </section>

  <hr>

  <!-- About -->
  <section class="about" id="about">
    <h2>About</h2>
    <p>Tomo Reynolds is a jazz pianist based in Toronto, currently in his third year of the Bachelor of Music program at <a href="https://mediaarts.humber.ca/programs/music-bachelor-of.html" target="_blank" rel="noopener noreferrer">Humber Polytechnic</a>. He has performed at venues including the <a href="https://www.therex.ca/" target="_blank" rel="noopener noreferrer">Rex Hotel Jazz & Blues Bar</a>.</p>
    <p>Available for jazz engagements, private events, and corporate functions, both as a solo pianist and in ensemble settings.</p>
  </section>

  <hr>

  <!-- Media -->
  <section class="media" id="media">
    <h2>Media</h2>
    <div class="video-embed">
      <iframe
        src="https://www.youtube.com/embed/MkrA7ZL8R4E"
        title="Tomo Reynolds performing at the Rex"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
      </iframe>
    </div>
    <ul class="media-links">
      <li><a href="https://www.youtube.com/@towmoe" target="_blank" rel="noopener noreferrer">YouTube</a></li>
      <li><a href="https://musescore.com/user/25260836" target="_blank" rel="noopener noreferrer">MuseScore</a></li>
    </ul>
  </section>

  <hr>

  <!-- Contact -->
  <section class="contact" id="contact">
    <h2>Contact</h2>
    <form class="contact-form" action="https://formspree.io/f/FORM_ID" method="POST">
      <label for="name">Name</label>
      <input type="text" id="name" name="name" required>

      <label for="email">Email</label>
      <input type="email" id="email" name="email" required>

      <label for="event-type">Event type</label>
      <select id="event-type" name="event-type">
        <option value="">Select...</option>
        <option value="jazz-venue">Jazz venue</option>
        <option value="private-event">Private event</option>
        <option value="corporate">Corporate function</option>
        <option value="other">Other</option>
      </select>

      <label for="date">Event date</label>
      <input type="date" id="date" name="date">

      <label for="message">Message</label>
      <textarea id="message" name="message" required></textarea>

      <button type="submit">Send</button>
    </form>
    <p class="contact-fallback">Or email directly: <a href="mailto:tomo@tomoreynolds.ca">tomo@tomoreynolds.ca</a></p>
  </section>

  <hr>

  <!-- Footer -->
  <footer>
    <ul class="social-links">
      <li><a href="https://ca.linkedin.com/in/tomo-reynolds-07992918a" target="_blank" rel="noopener noreferrer">LinkedIn</a></li>
      <li><a href="https://www.youtube.com/@towmoe" target="_blank" rel="noopener noreferrer">YouTube</a></li>
      <li><a href="https://musescore.com/user/25260836" target="_blank" rel="noopener noreferrer">MuseScore</a></li>
      <li><a href="https://ca.pinterest.com/tomoreyn/" target="_blank" rel="noopener noreferrer">Pinterest</a></li>
      <li><a href="https://www.reddit.com/user/tomoreyn/" target="_blank" rel="noopener noreferrer">Reddit</a></li>
    </ul>
    <p>&copy; 2025 Tomo Reynolds</p>
  </footer>

</body>
</html>
```

**Note:** Two placeholders to fill in later:
- `FORM_ID` in the Formspree action URL (needs a Formspree account)
- `tomo@tomoreynolds.ca` email (or whatever email Tomo prefers)

**Step 2: Commit**

```bash
git add index.html
git commit -m "Add single-page site: hero, about, media, contact, footer"
```

---

### Task 4: Create CNAME and update README

**Files:**
- Create: `CNAME`
- Modify: `README.md`

**Step 1: Create CNAME**

```
tomoreynolds.ca
```

**Step 2: Update README.md**

```markdown
# Tomo Reynolds Website

**URL:** https://tomoreynolds.ca/
**Repo:** Hosted on GitHub Pages (Brett's account initially)

## Tech Stack

Plain HTML/CSS. No build tools, no JavaScript dependencies. Google Fonts (EB Garamond). Formspree for contact form.

## Editing

- **Update bio:** Edit the About section in `index.html`
- **Add video:** Add a `<div class="video-embed"><iframe ...></div>` in the Media section
- **Add music platform:** Add `<li><a href="...">Platform</a></li>` to `.media-links`
- **Restyle:** Edit CSS custom properties in `:root` block of `style.css`
- **Update photo:** Replace `tomo.jpg`, keep the filename

## Deployment

Push to `main` branch. GitHub Pages auto-deploys.

## TODO

- [x] Design and build site
- [ ] Register domain (tomoreynolds.ca)
- [ ] Create Formspree account and update form action URL
- [ ] Set up GitHub Pages and DNS (Cloudflare)
- [ ] Get Tomo to review and rewrite bio
- [ ] Add Bandcamp/SoundCloud links when confirmed
- [ ] Add more YouTube embeds
- [ ] Deploy
```

**Step 3: Commit**

```bash
git add CNAME README.md
git commit -m "Add CNAME and update README with editing guide"
```

---

### Task 5: Create GitHub repo and push

**Step 1: Create repo on GitHub**

```bash
gh repo create BrettRey/tomoreynolds.ca --public --source=. --remote=origin --description="Tomo Reynolds - Jazz pianist website"
```

**Step 2: Push**

```bash
git push -u origin main
```

**Step 3: Enable GitHub Pages**

```bash
gh api repos/BrettRey/tomoreynolds.ca/pages -X POST -f source.branch=main -f source.path=/
```

(DNS and domain registration are separate manual steps outside this plan.)

---

### Task 6: Register domain

This is a manual/external step. Register `tomoreynolds.ca` through a registrar. Then configure DNS:

1. Add CNAME record: `tomoreynolds.ca` -> `brettrey.github.io`
2. Or use Cloudflare (matching brettreynolds.ca setup): proxy through Cloudflare, point to GitHub Pages IPs

Exact steps depend on registrar. This task is noted here for completeness but is not automatable.
