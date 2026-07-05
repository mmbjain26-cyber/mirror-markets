# Mirror Markets

Static site for Mirror Markets, hosted on GitHub Pages. Plain HTML and CSS, no build step.

## Structure

```
index.html                      homepage
css/site.css                    all styles, shared by every page
pairings/001-stripe-upi-pix.html  article pages, one file per pairing
favicon.svg                     mirrored MM mark
apple-touch-icon.png            iOS home-screen icon
assets/og.png                   social preview image (1200x630)
.nojekyll                       tells GitHub Pages to serve files as-is
```

## Publishing a new pairing

1. Copy the latest file in `pairings/` and rename it, e.g. `pairings/002-accenture-infosys-tcs.html`.
2. Update in the new file: `<title>`, both meta descriptions, the OG title/description/url, the canonical link, the pairing number, the pair line, the headline, the dateline, and the body.
3. Components available inside an article:
   - Paired stat with the seam: copy the `.stat-block` markup.
   - Data table: copy the `.data-table` markup. `class="num"` right-aligns a cell, `class="col-a"` colors it steel blue (developed), `class="col-b"` copper (emerging).
4. On `index.html`, promote the queue: move the new pairing into the Current Pairing section, and turn the previous one into a linked queue row by changing its `<div class="row">` to `<a class="row" href="pairings/00X-slug.html">`. Nothing inside the row needs to change.
5. Commit and push. Pages redeploys automatically.

## Design system (fixed)

- Paper `#F4F5F2`, ink `#171B18`, hairline `#DADCD5`. Accents only in pairs: steel blue `#33566B` developed, copper `#B4632A` emerging.
- Newsreader for display (italic for headlines), Hanken Grotesk for body, IBM Plex Mono for every number, label, and tag.
- The center seam is the signature. Vertical on desktop, horizontal on mobile. One load animation on the homepage hero only.

## Deploy

GitHub Pages serves from the `main` branch root. Settings > Pages > Source: Deploy from a branch, `main`, `/ (root)`.

After the site URL is final, replace every `USERNAME.github.io/mirror-markets` placeholder in `index.html` and the pairing pages (canonical + OG tags).

## Custom domain (when ready)

1. Buy the domain.
2. In the repo: Settings > Pages > Custom domain, enter the domain. GitHub creates a `CNAME` file in the repo.
3. At the DNS provider: for an apex domain (`mirrormarkets.com`), add four A records pointing to GitHub Pages IPs (185.199.108.153, .109.153, .110.153, .111.153); for `www`, add a CNAME record pointing to `USERNAME.github.io`.
4. Back in Settings > Pages, wait for the DNS check, then tick Enforce HTTPS.
5. Update the canonical and OG URLs in every page to the new domain.
