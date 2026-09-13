<div align="center">

# Ether.fi Cash

**A fast, single-page information site for the ether.fi Cash card.**

3% cashback on everyday spending · accepted anywhere Visa is accepted · free to open

[**→ View the live site**](https://web3cash.github.io/)

</div>

---

## What this is

A self-contained, static landing page that explains **ether.fi Cash** — a Visa card
that pays cashback on everyday purchases and is backed by a self-custody crypto
balance, so the money you have not spent keeps working instead of sitting idle.

The page is written to be understood in about **15 seconds**: one headline, one
subheadline, a handful of short benefit lines, an interactive cashback estimator,
an objection-handling FAQ, and a repeated call to action.

It is an **independent information resource**. It is not ether.fi's official
website. See [Disclosures](#disclosures).

## Live site

| | |
|---|---|
| **URL** | https://web3cash.github.io/ |
| **Hosting** | GitHub Pages, served from the repository root |
| **Canonical** | `https://web3cash.github.io/` |

## Features

- **Zero-build static page** — plain HTML, CSS and vanilla JavaScript in a single
  `index.html`. No framework, no bundler, no build step, no npm install.
- **Fully self-contained** — no third-party CSS, fonts, analytics or scripts.
  Zero outbound requests on page load.
- **Interactive cashback estimator** — arithmetic run entirely in the browser
  against the published cashback ladder. Nothing the reader enters leaves the page:
  no network call, no storage.
- **Works without JavaScript** — every section renders for a no-JS visitor and for
  crawlers that do not execute scripts. Motion and the estimator are progressive
  enhancements, never requirements for reading the page.
- **Accessible** — single `<h1>`, alt text on every image, a keyboard skip link,
  ARIA labels on icon-only controls, and respect for `prefers-reduced-motion`.
- **Responsive** — verified with zero horizontal overflow at 360, 390, 412, 768
  and 1280 px, with a sticky header and a sticky mobile call to action.
- **Sourced, honest content** — every figure is checked against ether.fi's own
  published materials and carries the date it was verified. Limits, fees and
  regional restrictions are stated, not hidden.

## Tech stack

| Layer | Choice |
|---|---|
| Markup | Hand-written HTML5, semantic sections |
| Styling | Modern CSS — custom properties, `clamp()` fluid type, grid, flexbox |
| Behaviour | Vanilla ES5-compatible JavaScript, no dependencies |
| Motion | CSS transitions + `IntersectionObserver` for scroll reveal |
| Imagery | WebP card art, SVG wordmark and store badges, PNG social card |
| SEO | Open Graph, Twitter card, JSON-LD (`WebSite`, `WebPage`, `FAQPage`) |
| Hosting | GitHub Pages (static) |

## Project structure

```
.
├── index.html                    # the entire site
├── assets/
│   ├── brand-logo.svg            # header wordmark
│   ├── card-core.webp            # primary card artwork
│   ├── card-black.webp           # secondary card artwork
│   ├── badge-app-store.svg       # App Store badge
│   ├── badge-google-play.svg     # Google Play badge
│   └── etherfi-cash-og.png       # 1200×630 social share card
├── robots.txt                    # crawler policy + sitemap reference
├── sitemap.xml                   # single-URL sitemap
├── .nojekyll                     # serve files as-is; skip Jekyll processing
└── README.md
```

Every asset path in `index.html` is **relative** (`assets/…`), so the page works
unchanged from the repository root, from a subfolder, or from any static host.

## Deploy

### GitHub Pages (root domain)

This site is designed to be served at the **root** of
`https://web3cash.github.io/`, which requires a repository named exactly
**`web3cash.github.io`**.

1. Create a repository named `web3cash.github.io` under the `web3cash` account.
2. **Upload every file and folder from this package to the repository root** —
   including the `assets/` folder, `robots.txt`, `sitemap.xml` and `.nojekyll`.
   The `.nojekyll` file is required: without it GitHub Pages runs Jekyll, which
   can skip files and directories beginning with an underscore or dot.
3. Open **Settings → Pages**. Under *Build and deployment*, set **Source** to
   *Deploy from a branch*, choose the **`main`** branch and the **`/ (root)`**
   folder, then save.
4. Wait for the first build to finish (usually under a minute). The site is then
   live at `https://web3cash.github.io/`.

> **Why the folder must be named `assets/` and the paths must stay relative:**
> GitHub Pages serves whatever is in the branch root as the site root. A path
> like `assets/card-core.webp` resolves to
> `https://web3cash.github.io/assets/card-core.webp`. If the images folder is not
> uploaded — or is uploaded outside the root — every image 404s while the HTML
> itself still loads, which is exactly the symptom this package was built to fix.

### Any other static host

The package is host-agnostic. Upload the contents to your web root, or serve the
folder directly:

```bash
python3 -m http.server 8080
# → http://localhost:8080/
```

### Making a versioned archive

```bash
zip -r etherfi-cash-github-pages.zip \
    index.html assets robots.txt sitemap.xml .nojekyll README.md
```

## Editing

Everything lives in `index.html` — styles in a `<style>` block in the head, behaviour
in a single `<script>` block before `</body>`. There is nothing to compile: edit the
file, refresh the browser.

Two conventions worth keeping if you maintain this page:

- **Never state an unsourced number.** Cashback rates, fees, APYs, limits and
  eligibility lists must be traceable to ether.fi's own current published terms,
  and the page records the date each was verified.
- **Keep the footnotes honest.** The affiliate disclosure, the "not financial
  advice" statement and the risk warning are part of the deliverable, not decoration.

## Disclosures

**Affiliate disclosure.** The links to sign up on this page — including the App
Store and Google Play badge buttons, which are routed to the sign-up page rather
than to an app-store listing — are affiliate links. The operator of this page
participates in the ether.fi Affiliate Program and may receive compensation when a
reader signs up through those links and reaches the programme's qualifying
activity threshold. It does not change the price or terms you receive. The
operator is not an employee, agent or representative of ether.fi, and this page is
not ether.fi's official website.

**Not financial advice.** Nothing here is financial, investment, legal or tax
advice, and nothing is a recommendation to buy, sell, stake, borrow against or
hold any asset. Every figure is a point-in-time snapshot taken on **13 September
2026**, and rates, eligibility and terms can change at any time without notice.

**Risk warning.** Staking, borrowing and holding digital assets involve
significant risk, including loss of your entire principal, slashing penalties,
smart-contract vulnerabilities, liquidation, and liquidity or redemption delays.
Rewards are variable and not guaranteed. ether.fi is not a regulated financial
institution; holdings are not bank deposits and are not FDIC-, SIPC- or otherwise
insured. Products and features are not available in all jurisdictions and are
subject to eligibility checks. The ether.fi Cash card is issued by a third party
and is not affiliated with the ether.fi protocol; separate issuer terms apply.

**Third-party material.** Card artwork, the ether.fi wordmark and the App Store
and Google Play badges are the property of their respective owners and are used
here to identify the products being described. This project is not associated
with, endorsed by or sponsored by ether.fi.

---

<div align="center">
<sub>An independent information page about the ether.fi Cash card. Not affiliated with ether.fi.</sub>
</div>
