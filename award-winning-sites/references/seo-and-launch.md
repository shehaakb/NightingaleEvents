# SEO and launch

## Head of every page
- `<title>`: "Service in City & Region | Brand". Under 60 characters.
- Meta description under 160 characters, with the mechanism and the city.
- Canonical URL, `theme-color` matching the paper colour, OG title, description, type, url, image (1200×630 with alt), `twitter:card summary_large_image`.
- Preconnect to Google Fonts, load only the weights used. Self-host fonts for production (Nightingale ships woff2 in `/fonts`).

## LocalBusiness JSON-LD
```json
{"@context":"https://schema.org","@type":"LocalBusiness","name":"…","description":"…","url":"…","telephone":"…",
 "address":{"@type":"PostalAddress","streetAddress":"…","addressLocality":"Mississauga","addressRegion":"ON","addressCountry":"CA"},
 "areaServed":[{"@type":"AdministrativeArea","name":"Greater Toronto Area"},{"@type":"City","name":"Brampton"},…],
 "sameAs":["https://instagram.com/…"],"openingHours":"Tu-Fr 11:00-19:00","priceRange":"$$"}
```
Pull address, hours and services from the owner's Instagram bio and Google profile; confirm which city they want to rank for when the studio address and the brand name disagree (B-Town is in Mississauga, brands as Brampton).

## On-page
- One H1. H2 per section with the service words in it.
- A service-area section and a footer sentence naming the towns.
- Alt text on real photos describing the work, not keywords.
- `robots.txt`, `sitemap.xml`, `llms.txt` (Nightingale ships all three).
- Lazy-load everything below the hero; `preload="none"` on videos with poster images; `data-src` plus IntersectionObserver for gallery clips.

## Performance
- Hero media loads after `load` plus 600 ms.
- Images resized to the largest rendered size (900 to 1200 px), JPEG quality 78 to 82, PNG only for transparency.
- A single CSS file and a single deferred script for sample builds; Vite for production builds with GSAP and Three.
- Film grain is an SVG data URI, not an image file.

## Asset prep recipes (Python + Pillow + numpy)
- **Background removal:** flood-fill from the edges over near-white pixels, respect existing alpha (transparent pixels often hide black RGB), soften the edge with a 0.8 px blur on the alpha, crop to the bounding box.
- **Brand duotone for a product photo:** percentile-stretch luminance (2nd to 98th), gamma 0.7, map 0→deep, 0.4→primary, 0.8→pale, 1→near white. Upscale 2× with Lanczos, light unsharp mask, if the source is small.
- **Card photos:** `ImageOps.fit` to 900×1200, centre on the subject.

## Deploy
Static, no build step, Netlify.
```
netlify login
netlify sites:create --name <brand>          # gives https://<brand>.netlify.app
netlify deploy --dir <folder> --prod
```
A `netlify.toml` at the repo root sets `publish` and long cache headers on `/assets/*`. Keep each client's site in its own folder of the award-winning-sites repo with a README row (folder, live URL, how to preview, how to deploy).

From a cloud session without Netlify network access, the Netlify connector can import a single self-contained HTML file from a claude.ai artifact URL; inline images as data URIs for that path. Prefer a local session with the CLI for the real multi-file deploy.

## Handoff checklist
- Placeholders replaced: name, phone, email, address, hours, prices, reviews, client logos.
- Forms wired: webhook endpoint set, hidden Netlify form mirrored, test submission received.
- Booking link set (Calendly or similar).
- Checkout connected if the site sells.
- Google Business Profile linked; sitemap submitted in Search Console.
- Owner has the repo, the Netlify site, and a one-paragraph "how to change copy" note.
