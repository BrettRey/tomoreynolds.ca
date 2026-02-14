# Tomo Reynolds Website Design

**Date:** 2026-02-14
**Domain:** tomoreynolds.ca (not yet registered)
**Hosting:** GitHub Pages (Brett's account initially, move to Tomo's later)

## Purpose

Booking-focused musician website with portfolio support. Primary goal: make it easy for venue bookers and event organizers to find Tomo, hear his playing, and contact him.

## Tech Stack

Plain HTML/CSS static site. No JavaScript, no build tools, no dependencies beyond Google Fonts. Matches brettreynolds.ca approach. Hosted on GitHub Pages with CNAME for custom domain.

## Architecture

Single-page scroll site with anchored sections.

### Sections (scroll order)

1. **Hero** -- Photo (at piano, stage lighting), name, tagline ("Jazz pianist. Toronto."), "Book me" CTA button scrolling to contact section.

2. **About** -- 2-3 paragraphs. Education at Humber (3rd year BA Music, piano). Gigging experience including student spots at the Rex. Available for private events, corporate functions, jazz venues. Versatile: ensemble and solo contexts.

3. **Media** -- YouTube embed (Rex performance: MkrA7ZL8R4E). Link to MuseScore profile. Structured so additional embeds (Bandcamp, SoundCloud, Spotify, more YouTube) can be added trivially.

4. **Contact** -- Formspree-powered form (name, email, event type, date, message). Direct email link as fallback. No CAPTCHA needed at current traffic levels.

5. **Footer** -- Social links: LinkedIn, YouTube, Pinterest, MuseScore, Reddit. Copyright.

### Files

```
tomo-website/
├── index.html
├── style.css
├── tomo.jpg
├── CNAME
├── README.md
└── docs/plans/
    └── 2026-02-14-website-design.md
```

## Typography and Colour

**"Same bones, jazzier feel"** variant of brettreynolds.ca. Designed for easy restyling via CSS custom properties.

- **Font:** EB Garamond (Google Fonts), Georgia fallback -- family consistency with brettreynolds.ca
- **Background:** Near-black (#1a1a1a) -- darker palette suits jazz/performance aesthetic
- **Text:** Warm off-white (#f0ead6)
- **Accent:** Warm amber/red pulled from the stage-lighting photo (~#c45a3c)
- **Links:** Accent colour, lighter on hover
- All colours defined as CSS custom properties for trivial restyling

## SEO

- Schema.org `Person` structured data (JSON-LD): name, url, sameAs (all social links), jobTitle, knowsAbout, alumniOf
- Open Graph meta tags for social sharing
- Semantic HTML5 elements throughout
- Descriptive `<title>` and `<meta name="description">`

## Future Additions (designed for but not built now)

- Google Calendar embed for upcoming gigs (placeholder section or add when gig density warrants it)
- Bandcamp/SoundCloud/Spotify embeds (when accounts confirmed)
- Additional YouTube embeds
- EPK/press kit section
- Photo gallery

## Domain and Hosting

1. Register tomoreynolds.ca
2. Create GitHub repo (Brett's account for now)
3. Enable GitHub Pages on main branch
4. Add CNAME file
5. Configure DNS (Cloudflare, matching brettreynolds.ca setup)
6. Later: transfer repo to Tomo's GitHub account (straightforward -- update DNS to point to new GitHub Pages URL, or fork and re-enable)

## Bio (draft, needs Tomo's input)

Placeholder bio for initial build. Tomo should review and rewrite in his own voice:

> Tomo Reynolds is a jazz pianist based in Toronto. Currently in his third year of the Bachelor of Music program at Humber Polytechnic, he has performed at venues including the Rex Hotel Jazz & Blues Bar. Available for jazz engagements, private events, and corporate functions.
