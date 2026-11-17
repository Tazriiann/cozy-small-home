# SEO Checklist — Cozy Small Home (homedecor.tazrian.me)

Applies the SEO research spec (Nov 17, 2026). Verified with `verify_blog.py` in this folder (re-run after any rebuild: `python3 verify_blog.py`). Last verified: Nov 17, 2026 — **PASS**.

## 1. Technical base (day 1)

- [x] **One canonical host** — `https://homedecor.tazrian.me` everywhere: every canonical, sitemap URL, internal link and `og:url`. No `www`, no `*.github.io`, no `tazrian.me/blog` variants linked anywhere.
- [x] **HTTPS** — all images, links and scripts use HTTPS. Taz must still tick **Enforce HTTPS** in GitHub Pages settings once the certificate is issued (see README).
- [x] **Sitemap** — hand-written `sitemap.xml`: exactly the indexable pages (home + About + 20 posts = 22 URLs), absolute URLs, accurate `<lastmod>2026-11-17</lastmod>`. No `<priority>` / `<changefreq>` (Google ignores them). Contact/Privacy/Disclaimer/404/archive are deliberately excluded — useful pages, not index targets.
- [x] **robots.txt** — `User-agent: *`, `Allow: /`, `Sitemap: https://homedecor.tazrian.me/sitemap.xml`. CSS/JS/images are not blocked.
- [x] **404.html** — custom not-found page at the root (GitHub Pages serves it automatically). Not in the sitemap.
- [x] **No orphans** — every post is 1 click from the homepage (featured grid + latest list) and linked from the footer/archive. `archive.html` (all-posts page, linked in the footer) is a second discovery path for crawlers and readers.
- [x] **URLs** — short, lowercase, hyphens, keyword-first, no dates, `.html` form used consistently in canonical/sitemap/internal links. Slugs were NOT changed to keyword-stacked forms (e.g. `/small-bedroom-ideas-renters-budget.html`): the current slugs are shorter and already keyword-first; changing them would add no ranking value. Do NOT change URLs after publishing.

## 2. Per-page head

- [x] **Title** — unique, 50–60 chars, keyword first on all 15 pages (measured: 50–59).
- [x] **Meta description** — unique, 120–160 chars, with the main keyword + a price/budget/audience detail (measured: 121–159).
- [x] **Canonical** — absolute, on every page, matching the chosen host.
- [x] **Open Graph + Twitter card** — `og:title`, `og:description`, `og:url`, `og:image` (1200×630 crop for posts and homepage), `og:type=article` on posts, `twitter:card=summary_large_image`, plus `og:image:width/height`.
- [x] **`meta robots max-image-preview:large`** — on every page (needed for Google Discover large cards).
- [x] **JSON-LD** — `BlogPosting` + `BreadcrumbList` + `FAQPage` on every post (single `@graph` block, validated as JSON); `WebSite` on the homepage only, **no SearchAction** (the site has no search). FAQPage markup is kept for AI/answer extraction — Google restricted FAQ rich results in Aug 2023, so do NOT expect SERP dropdowns. HowTo markup not used (rich results removed Sep 2023).
- [x] **Dates shown** — every post shows "Published November 17, 2026 · Updated November 17, 2026" plus reading time and an author byline linking to About. `datePublished`/`dateModified` are in the JSON-LD too. Only update `dateModified` when content substantially changes.

## 3. Keywords — dual-keyword strategy (taz, Nov 17)

Every post targets TWO keywords on the same page: the **primary** renter/budget long-tail (title/H1 — winnable in months 3–6) and the **secondary** plain broad term (intro, ≥2 H2s, alt text, internal-link anchors, FAQ — to climb for it as authority grows in months 6–12+). No separate post for the broad term (that would cannibalise).

| Post | Primary (winnable now) | Secondary (long-term, higher volume) |
|---|---|---|
| 15 Small Bedroom Ideas for Renters on a Budget | small bedroom ideas for renters on a budget | small bedroom ideas |
| Small Pantry Organization Ideas for Apartments | small pantry organization ideas for apartments | small pantry organization |
| 21 Budget Small Kitchen Organization Ideas for Renters | budget small kitchen organization for renters | small kitchen organization |
| 10 Small Bathroom Storage Ideas Under $25 | small bathroom storage under $25 | small bathroom storage |
| Small Living Room Makeover on a $200 Budget | small living room makeover on a $200 budget | small living room makeover |
| 12 Clever Storage Ideas for Tiny Apartments (pillar B) | clever storage for tiny apartments | small apartment storage ideas |
| How to Make a Small Room Look Bigger Without Painting (pillar A) | how to make a small room look bigger without painting | how to make a small room look bigger |
| 15 Small Apartment Decor Ideas for Renters on a Budget | small apartment decor ideas for renters on a budget | small apartment decor ideas |
| Best Small Space Furniture for Studio Apartments Under $200 | best small space furniture for studio apartments under $200 | small space furniture |
| Small Kitchen Before and After on a $200 Budget | small kitchen before and after on a $200 budget | small kitchen makeover |

- [x] Primary keyword in H1 (or all its words in order — list H1s read "…Ideas for…" so the exact phrase has "ideas" inside it), first paragraph, and ≥1 H2 per post. Secondary in lead, ≥2 H2s, alt text, incoming-link anchors and FAQ per post (verified by script).
- [x] **Deferred head term** — bare "best small space furniture" was narrowed to "best small space furniture for studio apartments under $200" (commercial intent, retailers dominate the bare term). Revisit after authority builds.
- [x] No keyword stuffing, no hidden text, no bought backlinks. US spelling throughout (organize/color/itemized).

## 4. Content clusters

- [x] **Cluster A — Small bedrooms & living** (pillar: *How to Make a Small Room Look Bigger Without Painting*): bedroom ideas → pillar + renters decor; renters decor → pillar + bedroom + living room; living-room makeover → pillar + furniture; furniture → pillar + living room + bedroom. Pillar links to all 4 supporting posts + cross-links to the Cluster B pillar.
- [x] **Cluster B — Small kitchens, bathrooms & storage** (pillar: *12 Clever Storage Ideas for Tiny Apartments*): pantry → pillar + kitchen organization; kitchen organization → pillar + pantry + before/after; before/after → pillar + kitchen organization; bathroom → pillar + pantry. Pillar links to all 4 supporting posts + cross-links to the bedroom post.
- [x] **3–5 contextual internal links in body copy per post** (verified: 3–9; pillars have 5 and 9), plus the "Related posts" box. Every supporting post links to its pillar in the first paragraphs. No orphans.
- [x] **Overlapping posts differentiated** — pantry = pantry closet/cupboard only (stated in the intro); kitchen organization = whole-kitchen systems (counters, drawers, cabinets, fridge); before/after = one real room's chronological transformation with the cost table ($250 full price, −$55 saving, $195 out of pocket).

## 5. Per-post template

- [x] 1 H1 per page; H2s as questions (or idea-group headings where a question is unnatural); H3s for sub-points.
- [x] Intro answers the query in 1–2 sentences with the primary keyword.
- [x] **40–60 word self-contained answer first under each question H2**, then detail (verified: all first paragraphs under question H2s are 48–60 words).
- [x] FAQ 4–6 Q&As at the end of every post (all have 5), mirrored in FAQPage JSON-LD.
- [x] Author byline linking to About; `datePublished` + `dateModified` shown.
- [x] Word counts — idea posts 1,200–2,000 words; narrow pantry how-to 800–1,200 words. Measured: bedroom 1,819; pantry 1,196; kitchen org 1,987; bathroom 1,840; living room 1,875; storage pillar 1,966; look-bigger pillar 1,964; renters decor 1,891; furniture 1,839; before/after 1,996. No padding to hit a count — Google has no preferred word count.
- [x] E-E-A-T: real prices as of Nov 2026, measurements, what worked/didn't, renter constraints. No fabricated author, credentials or AI headshot — the byline is the "Cozy Small Home" team page.

## 6. Images

- [x] Descriptive alt text, 80–125 chars (measured 85–105), keyword once, written for a screen reader.
- [x] `width` + `height` set on every image (prevents layout shift / CLS).
- [x] Hero eager (`loading="eager"`, `fetchpriority="high"`); below-fold images lazy-loaded.
- [x] Unsplash `?auto=format&fit=crop&w=1200&q=80` for heroes (≥1200px wide for Discover); homepage cards use `w=800` (displayed ~350px wide, roughly half the bytes). `auto=format` already negotiates WebP/AVIF in supporting browsers.
- [x] **Fixed Nov 17 09:36 — image file sizes:** the 2 heaviest heroes were downloaded and recompressed locally as WebP q60 at 1200x800: bedroom 285 KB -> 141 KB (`assets/small-bedroom-hero.webp`), furniture 303 KB -> 67 KB (`assets/best-small-space-furniture-hero.webp`, centre-cropped from square). Both now under the 200 KB hero target, still 1200 px wide for Discover. OG images are local JPG 1200x630 (130 KB / 77 KB). Other heroes remain remote Unsplash at w=1200&q=80, 90-200 KB.
- [x] **Partially applied — descriptive filenames / WebP files:** the 2 heaviest heroes are now local WebP files with descriptive names (`small-bedroom-hero.webp`, `best-small-space-furniture-hero.webp`). The other 8 heroes are still remote Unsplash URLs, so their filenames cannot be renamed. If original photos of taz's own space are added later, name them descriptively, resize to display size, compress to <100 KB content / <200 KB hero, and prefer WebP.

## 7. Core Web Vitals / mobile

- [x] Single small CSS file (~8 KB), no JavaScript on live pages (AdSense/GA4 scripts are commented out), system fonts only — no external fonts.
- [x] Targets: LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1. Field data can only be measured after launch — check PageSpeed Insights (mobile) and GSC's Core Web Vitals report once live.
- [x] Mobile-first: no horizontal overflow at 375 px (verified with headless Chromium on homepage + 2 posts, 375 px and 1280 px) or at 1280 px. Tap targets ≥ 48 px on nav links, buttons and share links.
- [x] No intrusive interstitials.

## 8. URLs

- [x] Short, lowercase, hyphens, keyword-first, no dates, `.html` form everywhere (canonical/sitemap/internal links). Do NOT change URLs after publishing — GitHub Pages has no server redirects (only meta-refresh + canonical).

## 9. Measurement — still needs taz (not done by Wally)

- [ ] **Google Search Console — Domain property for `tazrian.me`** via DNS TXT record (covers `homedecor.tazrian.me` automatically). Then submit sitemap, request indexing for home + 20 posts only. See README "After publishing".
- [ ] **GA4** — create a property, paste the Measurement ID (`G-XXXXXXXXXX`) into the commented-out GA4 block in `build.py`, re-run `build.py`, re-upload. Set retention to 14 months; link GSC ↔ GA4.
- [ ] **Bing Webmaster Tools** — same sitemap, verify via DNS TXT or HTML file.
- [ ] **Weekly GSC check** — queries at positions 8–30 (strengthen with a dedicated H2/FAQ + new detail, then request re-indexing); indexation; Core Web Vitals; Manual Actions (should stay empty).
- [ ] **PageSpeed Insights + Rich Results Test** — run every URL (mobile) after launch; fix anything "Poor".

## 10. Monetisation timing — do NOT apply for AdSense yet

- [ ] AdSense: wait until ~20–25 substantial posts + real organic traffic + ≥10 URLs indexed. "Low value content" is the commonest rejection on thin sites. See README.
- [ ] Affiliate (Amazon Associates / Impact / Awin): apply after the blog has 5–20 posts live. No affiliate links exist in the posts yet — product names are plain text on purpose. Needs taz: Payoneer account + W-8BEN tax form per network. **Open question: does taz already have a Payoneer account?**

## 11. Realistic timeline (new subdomain)

Indexing in days; impressions in 1–3 months; measurable Google traffic in 3–6 months; competitive terms in 6–12 months. Only a small minority of new pages reach the top 10 within a year. Pinterest is the bridge traffic for months 1–6 (2–3 fresh 1000×1500 pins per post, judge by outbound clicks).

## Verification summary (Nov 17, 2026)

- `verify_blog.py`: **PASS** — titles 50–60, descriptions 120–160, 1 H1/page, canonicals, OG/Twitter, `max-image-preview:large`, valid JSON-LD (BlogPosting + BreadcrumbList + FAQPage ≥4 Qs), sitemap = 22 URLs, no broken internal links, no British spellings, no affiliate hrefs, word counts in range, FAQ = 5/post, in-body links ≥3/post, broad keyword in lead/≥2 H2s/FAQ/incoming anchors, question-H2 answers 48–60 words.
- Local HTTP check: all 21 URLs return 200 (15 HTML pages + robots/sitemap/ads.txt/styles.css/logo/banner).
- All image URLs return HTTP 200 via curl; the 2 local heroes are now 141 KB and 67 KB, the other 8 Unsplash heroes 90–200 KB.
- Headless Chromium (Playwright): no horizontal overflow at 375 px or 1280 px on homepage, bedroom post and before/after post; screenshots read visually (homepage hero text collision fixed by swapping the baked-text banner for a plain Unsplash photo). Note: in this sandbox the Playwright browser's proxy blocks external hosts (`ERR_TUNNEL_CONNECTION_FAILED`), so Unsplash images render as alt text in screenshots only — real visitors load them fine (curl 200).
- Ad slots: 3 per post + 3 on homepage, all commented-out AdSense, `display:none` until activated — no blank gaps, no "Advertisement" placeholders.
