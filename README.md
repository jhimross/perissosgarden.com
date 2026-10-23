# Perissos Sustainable Garden — Website

The official one-page website of **Perissos Sustainable Garden**, a natural farm in Peñablanca, Cagayan, Philippines, practising permaculture, syntropic farming and natural farming.

> *Cultivating abundant life. Stewarding God's creation.*

- **Live site:** https://perissosgarden.com/
- **Email:** info@perissosgarden.com
- **Phone:** 0917 854 0644
- **Social:** @perissosgarden (Facebook, Instagram, YouTube, TikTok)

---

## Overview

A static, single-page site built with plain HTML, CSS and a little vanilla JavaScript. There is no build step, framework or database. Upload the folder to any web host and it works.

### Page sections (top to bottom)

| Section | Anchor | What it shows |
|---|---|---|
| Header | — | Logo, menu (collapses into a "Menu" button on phones), "Order now" button |
| Hero | `#top` | Headline "From our soil to your table", farm photo, methods, tagline with growing-sprout animation |
| Fresh produce + How to order | `#produce` | Chemical-free produce and the three ways to order |
| Farm products | `#products` | Pork, mushrooms, kardis, lemongrass, organic fertilizer, and four kombucha flavors |
| Our farm | `#methods` | Permaculture, syntropic farming, natural farming |
| Gallery | `#gallery` | 12 farm photos with a tap-to-enlarge viewer |
| The name | `#about` | John 10:10 and the meaning of *Perissos* |
| Contact | `#contact` | Contact details, social icons, Web3Forms contact form |
| Map | — | Full-width Google Map and "Get directions" button |
| Footer | — | Reverse logo, links, contact details |

---

## File structure

```
perissos-website/
├── index.html               The whole website (HTML, CSS and JS in one file)
├── README.md                This file
├── og-image.jpg             1200×630 social share image (Facebook, Messenger, X, Viber)
├── favicon.ico              Browser tab icon (16–64 px)
├── favicon-32.png           Browser tab icon
├── favicon-96.png           Icon used by Google Search results
├── apple-touch-icon.png     iPhone/iPad home-screen icon (180 px)
├── icon-192.png, icon-512.png   App icons (also used as the logo in Google's business data)
├── site.webmanifest         App name, colors and icons
├── .htaccess                Redirects http:// and www. to https://perissosgarden.com (Apache/LiteSpeed hosts)
├── robots.txt               Lets search engines crawl the site, points to the sitemap
├── sitemap.xml              List of pages for Google
└── assets/
    ├── perissos-mark.webp, perissos-mark-light.webp           Leaf-P mark (color / cream)
    ├── perissos-wordmark.webp, perissos-wordmark-light.webp   PERISSOS wordmark (color / cream)
    ├── hero-farm-600/900/1200/1448.webp   Hero photo in four sizes
    ├── pork.jpg, mushroom.jpg, pigeon-pea.jpeg,
    │   lemon-grass.webp, fertilizer.webp  "Also from the farm" card photos
    ├── kombucha-blue-ternate.webp, kombucha-moringa.webp,
    │   kombucha-roselle.webp, kombucha-turmeric-ginger.webp   Kombucha product photos
    └── gallery/                    12 gallery photos, each in 600 px and 1200 px
```

All image paths are **relative** (`assets/...`), so the site works from the domain root, a subfolder, or opened locally. Always keep `assets/` next to `index.html`.

---

## Deploying

1. Upload **everything inside** this folder to your web host's public folder (often `public_html` or `www`).
2. Make sure `favicon.ico`, `og-image.jpg`, `robots.txt` and `sitemap.xml` sit at the top level, e.g. `https://perissosgarden.com/favicon.ico`.
3. Turn on **HTTPS** (free SSL / Let's Encrypt) and redirect `http://` to `https://`.
4. After launch:
   - **Google Search Console:** add the site, submit `sitemap.xml`, and use *URL Inspection → Request indexing*.
   - **Facebook Sharing Debugger** (developers.facebook.com/tools/debug): paste the URL and click *Scrape Again* to refresh the share preview.
   - **PageSpeed Insights** (pagespeed.web.dev): check Core Web Vitals.
   - Claim and verify the farm's **Google Business Profile**.

If the domain changes from `perissosgarden.com`, update it in `index.html` (canonical link, `og:url`, `og:image`, `twitter:image`, structured data), `robots.txt` and `sitemap.xml`.

---

## Integrations

| Service | Where | Notes |
|---|---|---|
| **Google Analytics 4** | `<head>` of `index.html` | Measurement ID `G-PR7JD2F5W2`. Check *Reports → Realtime* after launch. |
| **Web3Forms** | Contact form | Sends messages to the email linked to the access key. Works only on the live site. Send a test message after launch. |
| **Google Maps embed** | Map section | Loads lazily. Blank in some previews (e.g. inside the Claude app) — normal; it shows on the live site. |
| **Google Fonts** | `<head>` | Marcellus (headings), Jost (body and labels), Caveat (one handwritten accent line). |

---

## Brand basics

| Token | Hex | Use |
|---|---|---|
| Sprout Green | `#689A36` | Mark, icons, shapes (not for small text) |
| Forest Green | `#3A603C` | Headings, links, primary buttons |
| Deep Canopy | `#2B4425` | Dark sections, footer |
| Bark Brown | `#6B4C25` | Script tagline, labels |
| Harvest Gold | `#E2A63B` | One highlight per section (e.g. "Order now") |
| Husk | `#F4F3EA` | Page background |
| Leaf Mist | `#E3EDCF` | Light panels |
| Soil Ink | `#1F2E1C` | Body text |

All colors are CSS variables at the top of the `<style>` block in `index.html` (`--forest`, `--canopy`, etc.). Full guidelines live in the **Perissos Brand System** and **Visual Identity** deck.

---

## SEO and social sharing

Already set up in `index.html`:

- Title: *Perissos Sustainable Garden | Natural Farm in Cagayan* (53 characters)
- Meta description, canonical URL, `lang="en-PH"`, geo tags for Peñablanca, Cagayan
- Open Graph and Twitter Card tags with `og-image.jpg` (1200×630, with alt text)
- Structured data (JSON-LD): `WebSite` (site name for Google) and `LocalBusiness` (address, map position, phone, email, social profiles). Products are listed in a `hasOfferCatalog` of plain `ListItem`s, **not** as `Product` items. Google requires every `Product` to have a price (`offers`), `review` or `aggregateRating`. Only switch to `Product` if you add real prices.
- Favicons in every size Google and phones ask for
- One `<h1>` containing the farm name and location; descriptive `alt` text on every photo

---

## Performance (Core Web Vitals)

- Hero photo is preloaded with `fetchpriority="high"` and served in four sizes via `srcset`.
- Every image has `width`/`height` set, so nothing shifts while loading (CLS ≈ 0).
- Photos below the hero use `loading="lazy"`; lower sections use `content-visibility:auto`.
- Images are WebP/JPEG, resized for their slot (product photos ~13–45 KB each).
- Local test on a throttled mobile connection: LCP ≈ 1.2 s, CLS 0.

---

## Animations and interactivity

All motion respects the visitor's **"reduce motion"** setting, and everything stays visible if JavaScript is off.

- **Growing sprout:** a seedling grows beside the hero tagline on load; leaves sway on hover.
- **Grow-in on scroll:** headings, cards and gallery photos rise into place in a staggered sequence.
- **Syntropic layers icon:** the three layers build one by one.
- **Squeeze a calamansi:** on the Blue Ternate kombucha card, the button drops a calamansi and the photo shifts from violet to pink, like real butterfly pea meeting citrus. "Pour a fresh glass" resets it.
- **Gallery viewer:** tap any photo to view it large (native `<dialog>`, closes with the button, a tap outside, or Esc).
- **Mobile menu:** the header menu collapses into a "Menu" button below 900 px.

---

## Common edits

All edits are in `index.html`.

| To change… | Look for |
|---|---|
| Phone / email | `0917 854 0644` and `info@perissosgarden.com` (contact section, footer, structured data) |
| A product's text | `<article class="good">` (farm products) or `<article class="flavor …">` (kombucha) |
| A product photo | Replace the file in `assets/` with the same name, or update its `src`, `width` and `height` |
| Gallery photos | `<figure class="g-item">` inside `#gallery`; add both a `-600.webp` and a `-1200.webp` version |
| Hero photo | `assets/hero-farm-*.webp` (four sizes) and the matching `<link rel="preload" as="image">` in `<head>` |
| Brand colors | CSS variables at the top of the `<style>` block |
| Search title / description | `<title>`, `<meta name="description">`, and the `og:` / `twitter:` tags |

Tip: resize new photos before uploading (600–1200 px wide, WebP or JPEG at ~70–80% quality). Phone photos straight from the camera are 3–6 MB and slow the page down.

---

## Still to fill in

- [ ] Usual reply time — the placeholder **[1–2 days]** appears twice (How to order, Contact)
- [ ] Confirm the harvest-list day ("posted every Friday") and pick-up / delivery areas
- [ ] Confirm the mushroom varieties listed (oyster, straw, wood ear)
- [ ] Verify each social link opens the right @perissosgarden profile

---

## Compliance notes

- Products are described as **"naturally farmed, no chemicals"**. Use **"organic"** on labels or claims only after certification (RA 11511; third-party or PGS).
- Health-benefit wording (e.g. blood pressure, anti-inflammatory) was left out on purpose. Check with **FDA Philippines** before adding such claims for kombucha or other processed products.
- Selling fertilizer generally requires registration with the **Fertilizer and Pesticide Authority (FPA)**.
- Get consent before posting photos of identifiable visitors.

---

© Perissos Sustainable Garden · Peñablanca, Cagayan, Philippines
