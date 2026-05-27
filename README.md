# Will Reynolds

Solo operator behind **Apex Strategy & Media** — I build and run a portfolio of performance-grade web properties end-to-end, from architecture through deployment, plus the self-hosted infrastructure underneath them and open livability research for Thailand.

## Apex Strategy & Media

**[Apexstm.com](https://apexstm.com)** — performance-first websites for local service businesses. PSI 90+ guaranteed, the client owns everything, no monthly platform fee. One operator, no agency overhead. Apex clients get a standalone build, delivered as source they own outright — no platform lock-in.

For my own portfolio I run an Astro + Cloudflare monorepo as a site factory: every property inherits CI/CD, typed schema.org markup, lead capture, and a Lighthouse-CI deploy gate on day one. A vertical registry adds a new market (HVAC, roofing, lawn care, fishing) without touching code; shared packages handle schema builders with safe JSON-LD escaping, map facades, and a test layer that scans for forbidden patterns and asserts on build output (one `h1`, valid JSON-LD, absolute canonicals, dimensioned images, skip links). Hard rules — PSI ≥ 90, LCP ≤ 2.5s, total page weight ≤ 700KB, Turnstile server-side verification, Biome strict mode, path-filtered deploys per site — enforced by CI, not by intention.

## Properties I build and run

Live properties built and operated to a single engineering standard — real Lighthouse scores, not estimates.

**[Brazosport Fishing Guide](https://apexstm.com/projects/brazosport-fishing-guide/)** — a data-driven guide to the Freeport/Brazosport charter fishing scene, and the most interesting build in the portfolio. Four things it does that most sites don't:

- **Build-time solunar scoring.** A model computes and scores lunar feeding windows 0–100 at build time — weighting major over minor peaks, sunrise/sunset overlap, and moon-phase strength — and renders the top-five ranked windows for the next 14 days as static HTML with zero client JavaScript. The headline answer ("when should I fish?") is precomputed on every deploy.
- **Click-gated charting.** The 7-day tide-and-solunar chart code-splits Chart.js into its own chunk and only fetches it on user click, so the page hits PSI 100 on first load. A Playwright test fails the build if the chart library loads before the click.
- **Multi-source edge data with outage resilience.** NOAA tide predictions (KV-cached 24h), Open-Meteo marine and wind, and the NWS narrative forecast are merged at the edge; if a feed goes down the component shows a provider-named notice while the math-based solunar list keeps rendering.
- **Lead-capturing cost estimator.** A three-step charter estimator fires a partial lead the moment a visitor blurs the email field — capturing trip context before full submission — and restores progress from local storage for seven days.

Mobile 92 performance / 100 accessibility, best-practices, and SEO; desktop 100 across all four; 312KB total page weight; zero cookies; eight schema types.

**[WJR Visuals](https://apexstm.com/projects/wjr-visuals/)** — the Media half of Apex: a cinematic scrollytelling portfolio for documentary travel photography published in The Guardian, U.S. Army, and Photo-Weekly Germany. Lenis-driven smooth scroll powers full-screen reveals without a heavy animation library; navigation reads scroll velocity and direction; imagery is art-directed with separate landscape and portrait crops per image. Reduced-motion is fully respected — Lenis is disabled entirely and reveals snap to their finished state. Re-platformed from Next.js / Vercel to Astro 6 + Cloudflare Workers for a lighter runtime and no vendor lock-in, with build-time AVIF/WebP generation at four widths per image and Cloudflare D1 for contact leads.

**[Georgetown Lawn Guide](https://apexstm.com/projects/georgetown-lawn-guide/)** — a lawn-care pricing guide for Georgetown, TX, backed by Texas A&M AgriLife Extension data; perfect desktop Lighthouse, LCP 1.1s.

**[New Braunfels AC Guide](https://apexstm.com/projects/newbraunfels-ac-guide/)** — an HVAC consumer guide with verified pricing and TDLR license-check walkthroughs; under 200KB total page weight, LCP 0.6s.

## Infrastructure I run

A VPS runs analytics, error monitoring, contracts, CRM, uptime monitoring, a log viewer, and a form-capture API for my own portfolio of sites. Each service runs in its own container with a dedicated Postgres user against a shared Postgres instance, least-privilege throughout. Umami handles analytics; GlitchTip handles error monitoring (deliberately swapped in for Sentry SaaS to keep the observability stack on owned infrastructure); Twenty handles CRM; DocuSeal handles contracts and signatures; Gatus drives public status pages; Caddy handles TLS and routing.

The `leads` service is the custom piece: several of my own sites POST into a single FastAPI + asyncpg endpoint. Per-project CORS allow-lists from a single source of truth, Turnstile server-side verification, IP-hash rate limiting, and Postgres advisory locks for migration serialization. CRM and email fan-out are best-effort — each step (validation, Turnstile, database write, CRM + email) can fail independently without losing the submission. One service, many sites; one fix, every site benefits. (Distinct from the per-site client-owned lead capture above — this one feeds my own portfolio.)

## Stack

TypeScript + Astro on the frontend; Python (FastAPI, asyncpg, DuckDB) on the backend; Postgres + object storage for state; Cloudflare Workers and a self-managed VPS for compute; Caddy and Docker Compose for the platform underneath. pnpm workspaces and Biome for monorepo discipline; self-hosted Umami and GlitchTip for analytics and error monitoring.

## Open research and data work

**[Thailand Livability Index](https://thailandliveabilityindex.com)** is open research: a province-level composite livability index for Thailand across multiple categories, sourced from public government and civic datasets and cited from day one. Ingestion runs through a Python ETL pipeline backed by DuckDB for analysis and Cloudflare R2 for artifact storage; normalization uses a documented goalpost methodology, with a reproducibility check gating any score before it can be published. The point of the project is that the methodology, the supporting data, and a versioned **public API with embeddable widgets** are all open — the research is the deliverable, not a black box. In active development.

**[thailand-canonical-admin-names](https://github.com/DevelopedbyWill/thailand-canonical-admin-names)** — a concrete open artifact supporting that work: canonical English and Thai names for Thailand's administrative units at all three levels, with TIS-1099 and ISO 3166-2 codes, an override registry, computed centroids, and bundled polygons. CC BY 4.0, Zenodo DOI.

## Background

20-year USAF career, transitioned into web and data engineering post-military. AWS Certified Cloud Practitioner. Microsoft Certified: Azure Administrator Associate. CompTIA Security+, Network+, A+. MBA in progress. Building things that are live and used, not demo repos.

## Connect

[Apexstm.com](https://apexstm.com) for inquiries.
