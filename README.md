# Tomo Reynolds Website

**URL:** https://tomoreynolds.ca/
**Repo:** GitHub Pages on Brett's account (`BrettRey/tomoreynolds.ca`); Tomo (`tomoreyn`) is a collaborator and edits directly on GitHub.

## Tech Stack

Plain HTML/CSS. No build tools, no JavaScript, no external dependencies.

## Structure

Tomo's design (May 2026): the home page is a single full-width artwork (`Background.jpg`) with three buttons laid over it, each leading to its own page.

```
index.html      home: Background.jpg canvas + three buttons
about.html      bio, YouTube embed, music links
contact.html    email link, social links
lessons.html    private lessons (stub: no rates or details yet)
404.html        not-found page pointing back home
style.css       1. canvas + buttons (desktop), 2. phone overrides, 3. inner pages
Background.jpg  the artwork (resized for the web; the original 2480x3508 is in git history)
tomo.jpg        photo from the February single-page design (currently unused)
CNAME           custom domain
```

The February single-page design is preserved on the `archive/single-page-2026-02` branch.

## Editing

- **Home-page buttons:** the links in `index.html` are styled text (`.link-element.text-btn` in `style.css`) because the button images Tomo's design referenced (`about-btn.jpg`, `contact-btn.jpg`, `lessons-btn.jpg`) were never uploaded. To use images: upload them, put `<img src="about-btn.jpg" alt="About Me">` inside each link, and remove the `text-btn` class.
- **Bio:** edit `about.html`.
- **Lessons details (rates, levels, location):** edit `lessons.html`.
- **Add a video:** copy the `<div class="video-embed">` block in `about.html`.
- **Add a music platform:** add an `<li>` to `.page-links` in `about.html` or `contact.html`.
- **Replace the artwork:** replace `Background.jpg`, keep the filename and the portrait orientation. Resize to about 2000 px wide before uploading; the phone layout scales it to 220% of the screen width, so it needs the resolution but not the full print file.
- **Restyle inner pages:** section 3 of `style.css`.

## Deployment

Push to `main`. GitHub Pages deploys automatically (`gh api repos/BrettRey/tomoreynolds.ca/pages/builds/latest` shows the status).

**HTTPS:** DNS (Cloudflare, DNS-only) points at GitHub Pages. The certificate was issued on 2026-10-26 and Enforce HTTPS is on. If it ever lapses (`gh api repos/BrettRey/tomoreynolds.ca/pages --jq .https_certificate`), remove and re-add the custom domain (Settings > Pages, or `gh api -X PUT repos/BrettRey/tomoreynolds.ca/pages` with `cname` null then `cname` set), wait for the state to become `approved`, then re-enable **Enforce HTTPS**.

## TODO

- [ ] Tomo: upload the three button images, or keep the text buttons
- [ ] Tomo: fill in `lessons.html`
- [ ] Contact is email-only; a Formspree form was planned in February but never set up
- [ ] Add Bandcamp/SoundCloud links when confirmed
