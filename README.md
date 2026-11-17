# Cozy Small Home — blog.tazrian.me

A complete, professional, static blog for Cozy Small Home (Pinterest @thecozysmallhome).
Budget home decor for small apartments and tiny rooms, US audience.

## What is in this folder

- `index.html` — homepage (hero, featured posts, category cards, latest posts)
- `about.html`, `contact.html`, `privacy-policy.html`, `disclaimer.html` — real pages, required for AdSense
- `posts/` — 10 full posts (idea posts 1,200–2,000 words; the narrow pantry how-to 800–1,200 words)
- `styles.css` — one shared stylesheet, mobile-first
- `assets/logo.png` — profile-picture house logo
- `assets/banner.png` — living-room banner (also used as the homepage hero)
- `CNAME` — contains `blog.tazrian.me`
- `ads.txt` — placeholder publisher ID, must be replaced after AdSense approval
- `robots.txt`, `sitemap.xml` (home + About + 10 posts only — the indexable pages)
- `404.html` — custom not-found page (GitHub Pages serves it automatically)
- `archive.html` — all-posts archive page, a second discovery path for readers and crawlers
- `SEO-CHECKLIST.md` — the full SEO checklist: what was applied and what still needs taz
- `build.py` + `posts_content.py` — the generator that assembles the pages (not needed on the live site; safe to upload, or delete before uploading)

## Where will the ads be? — no blank spaces

There are **no empty ad boxes, no "Advertisement" placeholders, and no blank gaps** on the live site right now.

AdSense code is present in the HTML but **commented out**, and the CSS rule is:

```css
.ad-slot { display: none; min-height: 0; }
```

So an empty slot takes up zero space. Sections flow together exactly as if there were no ads at all. That is the answer to the question "will there be spaces left in between sections?" — **no, not until ads are turned on, and then Google fills the slot**.

### The 3 ad slots (in every post, and on the homepage)

1. **Leaderboard / banner — below the header**
   - Homepage: directly below the hero image.
   - Posts: directly below the post title and affiliate-disclosure box.
   - This is the most visible slot; Google usually fills it with a banner or responsive ad.
2. **In-article — after about 500 words / after the 2nd section**
   - `build.py` inserts this slot right after the first paragraph following the 2nd H2.
   - It is the highest-earning in-article position on most blogs.
3. **In-article — before the conclusion / FAQ**
   - `build.py` inserts this slot immediately before the FAQ heading, just before the reader finishes.

There is also an **Auto Ads script in `<head>`**, commented out. Auto Ads lets Google decide placements automatically. Use *either* Auto Ads *or* the manual slots — not both at first, or ads will double up.

> Note on slot (2)/(3) placement: `build.py` inserts the commented-out in-article slots programmatically — slot 2 after the first paragraph following the 2nd H2 (~500 words in), slot 3 immediately before the FAQ heading. Both are labelled in the HTML comments.

## How to activate AdSense later (only after approval)

**Do NOT apply for AdSense at 10 posts.** Google publishes no minimum, but the community-observed reliable floor is ~15–25 substantial (800–1,000+ word) original posts, About/Privacy/Contact pages, HTTPS, at least 10 URLs indexed in Google Search Console, and some real organic traffic. "Low value content" is the commonest rejection. Wait until the blog has ~20–25 posts plus real organic traffic, then apply. Ads also slow the site (Core Web Vitals) — another reason to delay.

1. Apply at adsense.google.com with the site `blog.tazrian.me` — only once the conditions above are met.
2. When approved, Google gives you a publisher ID like `ca-pub-1234567890123456`.
3. In every HTML file: find `ca-pub-0000000000000000` and replace it with your real ID, and remove the `<!--` and `-->` around the AdSense blocks you want to use. Then add the class `active` to the slot, or change the CSS to `.ad-slot.active { display:block; }` — the stylesheet already includes `.ad-slot.active`.
4. In `ads.txt`: replace `pub-0000000000000000` with the digits after `ca-pub-` in your publisher ID. Keep the rest of the line identical.
5. Push the changes to GitHub. Ads appear within a few hours to a day.

## How to publish to GitHub Pages

1. **Create a new repo** on GitHub (do NOT use `Tazriiann.github.io` — that is the portfolio). Name it e.g. `cozy-small-home` or `blog`.
2. **Upload everything in this folder** to the repo root (index.html, styles.css, about.html, contact.html, privacy-policy.html, disclaimer.html, posts/, assets/, CNAME, ads.txt, robots.txt, sitemap.xml). Upload via the GitHub web UI: Add file → Upload files, then Commit. `build.py` / `posts_content.py` can be left out.
3. **Turn on Pages:** repo → Settings → Pages → Source: Deploy from a branch, Branch: `main`, Folder: `/ (root)`. Save.
4. **Custom domain:** in Pages settings, set Custom domain to `blog.tazrian.me` and save. GitHub will write the CNAME for you (the CNAME file is already here as a backup).
5. **DNS:** in the DNS settings for `tazrian.me`, add a CNAME record: host `blog` → `Tazriiann.github.io` (your GitHub Pages address). Do NOT change the existing records for `tazrian.me` itself.
6. **Wait:** DNS + the HTTPS certificate usually take 15 minutes to a few hours (up to ~24 h for the certificate). Then open https://blog.tazrian.me — it should show the homepage.
7. **Enforce HTTPS:** in Pages settings, tick **Enforce HTTPS** — but only once the certificate is ready (the checkbox appears after it is issued). All images and links on the site already use HTTPS.
8. **Claim the site on Pinterest** (Settings → Claim) once it is live, and add the blog link to the Pinterest profile.

## SEO — what is baked in

Every page has:
- `<title>` 50–60 characters, keyword first, unique per page (e.g. "15 Small Bedroom Ideas for Renters | Cozy Small Home")
- `<meta name="description">` 120–160 characters, unique per page, with the main keyword and a price/budget/audience detail
- `<meta name="robots" content="max-image-preview:large">` (needed for Google Discover large cards)
- One `<h1>` per page (the post title), H2s as questions with a 40–60-word direct answer first, H3s for sub-points; the keyword appears naturally in the H1, first paragraph and 1–2 H2s — no stuffing, no hidden text
- Absolute canonical link to its own `blog.tazrian.me` URL; one canonical host everywhere
- Open Graph + Twitter card meta (title, description, image — post images are 1200×630 crops for social cards)
- JSON-LD: `BlogPosting` + `BreadcrumbList` + `FAQPage` on every post, `WebSite` on the homepage only (no SearchAction — the site has no search). FAQPage markup is kept for AI/answer extraction; Google restricted FAQ rich results in Aug 2023, so do not expect SERP dropdowns.
- Descriptive image alt text (80–125 chars, broad keyword included once), `width`/`height` set to prevent layout shift, hero image eager, below-fold images lazy-loaded; Unsplash images use `?auto=format&fit=crop&w=1200&q=80` — `auto=format` already negotiates WebP/AVIF in supporting browsers (forcing `&fm=webp` measured larger: 351 KB vs 285 KB JPEG, so it is not used); og:image is a 1200×630 crop
- Content clusters: Cluster A (bedrooms & living, pillar "How to Make a Small Room Look Bigger Without Painting") and Cluster B (kitchens, bathrooms & storage, pillar "12 Clever Storage Ideas for Tiny Apartments"). Every post has 3–5 contextual internal links in body copy, links to its pillar in the first paragraphs, and the pillars link to all their supporting posts. No orphan pages; every post is 1–2 clicks from the homepage, plus an `archive.html` page as a second discovery path.
- Keywords retargeted at long-tail, modifier-stacked phrases (room + renter/budget/under-$X), e.g. "small bedroom ideas for renters on a budget", "small bathroom storage under $25", "small living room makeover on a $200 budget". The bare head term "best small space furniture" was deferred and narrowed to "best small space furniture for studio apartments under $200".
- **Dual-keyword strategy (taz, Nov 17):** every post targets TWO keywords on the same page — the primary renter/budget long-tail (in title/H1, winnable in months 3–6) AND the plain broad term (used naturally in the intro, at least 2 H2s, alt text, internal-link anchors and FAQ, to climb for it as the site gains authority in months 6–12+). No separate post for the broad term — that would cannibalise. See `SEO-CHECKLIST.md` for the primary + secondary keyword per post.
- Clean URLs, short, lowercase, hyphens, keyword-first, `.html` form used consistently in canonical/sitemap/internal links; `sitemap.xml` lists exactly the indexable pages (home + About + 10 posts) with accurate lastmod; `robots.txt` is `Allow: /` + Sitemap line; `404.html` included
- Fast: one small CSS file (~8 KB), no JavaScript at all on the live pages (AdSense/GA4 scripts are commented out), system fonts only — no external fonts. Targets: LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1; tap targets ≥ 48 px on nav/buttons/share; no horizontal scroll at 375 px

## After publishing — Google Search Console + Analytics (taz does this)

1. **Google Search Console — Domain property (do this first):** go to search.google.com/search-console → Add property → **Domain** → enter `tazrian.me` (bare domain, no `https://`). Verify once via the **DNS TXT record** at the domain registrar/DNS host. A Domain property covers every subdomain and protocol, so `blog.tazrian.me` is included automatically — no second verification, no meta tag needed. (A URL-prefix property for `https://blog.tazrian.me/` would NOT cover the root domain.)
2. **Submit the sitemap:** in GSC, Indexing → Sitemaps → enter `https://blog.tazrian.me/sitemap.xml`. Status should become "Success".
3. **Request indexing for the homepage + each of the 10 posts only:** URL Inspection → paste URL → "Request indexing". Do the 10 most important pages only; Google limits daily requests, repeat requests do not speed things up, and a request does not guarantee indexing.
4. **Google Analytics 4:** create a GA4 property + web data stream, copy the Measurement ID (`G-XXXXXXXXXX`), and paste it into the commented-out GA4 block in `build.py` (`GA4_HEAD`), then re-run `build.py` and re-upload. Set data retention to 14 months. Link GSC ↔ GA4 (GA4 Admin → Product links → Search Console links).
5. **Bing Webmaster Tools** (free): add the site, verify with the same DNS TXT record or an HTML file, submit the same sitemap. Bing powers some AI surfaces.
6. **Weekly GSC check (15 min):** Performance → Search results — watch for target queries at positions 8–30 (near-wins to strengthen with a dedicated H2/FAQ + a paragraph of new detail, then request re-indexing). Indexing → Pages — investigate "Crawled – currently not indexed" (thin/duplicate content) and "Discovered – currently not indexed" (improve internal linking + content). Check Core Web Vitals + Mobile Usability, fix "Poor" URLs first.

## Realistic timeline (new subdomain — do not expect fast Google traffic)

| Phase | When | What to expect |
|---|---|---|
| Setup + indexing | Week 1–2 | Sitemap submitted, pages crawled; homepage + posts indexed within days if requested; brand name ranks |
| Sandbox / trust-building | Months 1–3 | Impressions appear in GSC for long-tails; rankings mostly beyond position 50; Pinterest clicks begin within weeks |
| Early traction | Months 3–6 | Long-tail keywords rank positions 20–50, some page 2; first steady Google clicks |
| Measurable growth | Months 6–12 | Competitive terms start ranking 6–9 mo; 20+ posts + a few backlinks compound |
| Authority | 12–24 mo | Head terms become reachable; AdSense/monetisation realistic |

Pinterest is the bridge traffic for months 1–6: 2–3 fresh pins per post (1000×1500, keyword in title/description/filename), a few per week, each linking to its specific post — judge by outbound clicks, not followers/saves.

## After publishing — content

- Make 2–3 fresh Pinterest pins per post, linking to the post URL (not the homepage).
- Publish 1–2 new posts per week inside the same two clusters until ~25 posts (next: "small bedroom storage", "renter-friendly small kitchen upgrades", "small bathroom organization under $50", "small living room layout", "small apartment entryway ideas").
- Affiliate: no affiliate links are in the posts yet — product names are plain text on purpose. Add real links only after joining Amazon Associates / Impact / Awin, and keep the disclosure box at the top of each post.
- Refresh evergreen posts every 6–12 months in place (prices first — "under $25" goes stale fastest). Never change a published URL; only update `dateModified` when the content substantially changed.
