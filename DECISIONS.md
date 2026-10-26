# Decisions: tomoreynolds.ca
<!-- SUMMARY: decision log for Tomo's website · status: live over https · updated: 2026-10-26 -->

2026-10-26 — Keep Tomo's May 2026 canvas design as the site; the February single-page design is archived on branch `archive/single-page-2026-02`.

2026-10-26 — Replace the three missing button images with styled text buttons (`.link-element.text-btn`) rather than drawing new images. The images were never uploaded (searched: repo history, remote refs, forks, Tomo's gists, Spotlight, `~` to depth 4, Gmail from tomoreyn@gmail.com); the links and classes are kept so images can be dropped back in.

2026-10-26 — Write `about.html`, `contact.html`, `lessons.html` from the February site's own content (bio, YouTube embed, links). Dropped "third year" from the bio because it dated from February 2026. `lessons.html` is a stub: no source exists for rates, levels, or location.

2026-10-26 — Contact is a mailto link to tomoreyn@gmail.com. The Formspree form was never given a form ID, so email is the only working channel.

2026-10-26 — `Background.jpg` resized from 2480x3508 (1.8 MB) for the web; original retained in git history.

2026-10-26 — HTTPS: the custom domain was removed and re-added through the Pages API to trigger certificate issuance (the domain had been added in February with no certificate ever issued); the certificate was approved within minutes and Enforce HTTPS enabled.
