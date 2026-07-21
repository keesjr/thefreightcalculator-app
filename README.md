# thefreightcalculator.app

Free browser-based freight calculators from **Freight Calculator** by Sea &amp; Shore Services. Every calculation runs client-side — no signup, no data leaves the browser.

**Live:** https://www.thefreightcalculator.app/
**Brand site:** https://www.thefreightcalculator.ai/
**Android app:** https://play.google.com/store/apps/details?id=com.seaandshoreservices.freightcalculator

## The six tools

| Tool | What it does |
| --- | --- |
| **CBM calculator** | Carton dimensions (cm/mm/m/in) → cubic metres per carton and total shipment volume |
| **Chargeable &amp; volumetric weight** | Compares gross weight against volumetric weight across five mode divisors |
| **Container load calculator** | Fill percentage by volume and payload for 20ft, 40ft and 40ft High Cube, plus containers required |
| **Loading metre (LDM)** | European road freight floor space, trailer percentage and chargeable weight, with stacking |
| **Freight cost estimator** | Lane rate plus THC, BAF, customs clearance and documentation → all-in cost |
| **Cargo density** | kg/CBM and lb/ft³, with a verdict on whether cargo will be weight- or volume-billed |

Each tool returns a plain-English verdict alongside the numbers — e.g. whether you are paying for air, whether FCL beats LCL, or whether you are weight- or volume-limited in the box.

## Reference values used

```
CBM               = L(m) × W(m) × H(m) × qty
Volumetric weight = CBM × divisor
Chargeable weight = max(gross weight, volumetric weight)

Divisors    air 167 kg/CBM (IATA 1:6000) · courier 200 kg/CBM (1:5000)
            sea LCL 1000 kg/CBM (W/M)    · EU road 333 kg/CBM

Containers  20ft      ~28 CBM usable / 28,000 kg
            40ft      ~58 CBM usable / 26,500 kg
            40ft HC   ~66 CBM usable / 26,000 kg
            45ft HC   ~76 CBM usable / 27,700 kg

LDM         (L(m) × W(m) / 2.4) × qty / stack layers
            standard trailer = 13.6 LDM · 1 LDM ≈ 1750 kg

FCL vs LCL break-even ≈ 13–15 CBM
```

Figures are industry standards for quoting and planning. Always confirm exact capacities and divisors with your carrier before booking.

## What's here

Single-page, zero-dependency static site — no build step, no framework, no external requests.

| File | Purpose |
| --- | --- |
| `index.html` | Markup, inline CSS, all six calculators in vanilla JS, and JSON-LD |
| `assets/` | App icon and screenshot |
| `CNAME` | Custom domain for GitHub Pages |
| `robots.txt` | Crawl rules, incl. explicit allows for AI/LLM crawlers |
| `sitemap.xml` | XML sitemap with per-tool anchors |
| `llms.txt` | Tool list and reference formulas for AI search engines |
| `site.webmanifest` | PWA manifest |
| `favicon.svg` | Inline vector favicon |
| `404.html` | Branded not-found page |
| `.nojekyll` | Serves files as-is on GitHub Pages |

## SEO implementation

- **Structured data** — JSON-LD `@graph` with `Organization`, `WebSite`, `WebApplication` (feature list, free-to-use offer), two `HowTo` entities (calculating CBM, calculating chargeable weight), `FAQPage` and `BreadcrumbList`.
- **Head tags** — canonical, robots directives, `hreflang` incl. `x-default`, Open Graph and Twitter cards.
- **Targeting** — the calculators own high-intent queries ("cbm calculator", "chargeable weight calculator", "how many cbm in a 20ft container") that free utilities rank and earn links for; every tool cross-links to the brand site to pass authority both ways.
- **Core Web Vitals** — inlined CSS/JS, system font stack, explicit image dimensions, page weight under 200 KB.
- **Accessibility** — skip link, labelled form controls, semantic landmarks, visible focus rings, `prefers-reduced-motion` support.

## Deploying

GitHub Pages serves `main` from the repository root. Push and it is live within a minute.

DNS should point at GitHub Pages:

```
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153
CNAME www   keesjr.github.io
```

Note that `.app` is on the HSTS preload list, so HTTPS is mandatory — enable **Enforce HTTPS** in Settings → Pages as soon as the certificate is issued, or the site will not load at all.

## Post-launch checklist

1. Verify the domain in [Google Search Console](https://search.google.com/search-console) and submit `sitemap.xml`.
2. Do the same in [Bing Webmaster Tools](https://www.bing.com/webmasters).
3. Run the [Rich Results Test](https://search.google.com/test/rich-results) to confirm HowTo and FAQ eligibility.
4. Check [PageSpeed Insights](https://pagespeed.web.dev/) for mobile LCP/INP/CLS.
5. Share individual tools on logistics forums and communities — free calculators are the most link-worthy asset here.

## Licence

© Sea &amp; Shore Services. All rights reserved.
