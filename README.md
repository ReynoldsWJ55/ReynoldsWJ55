# Will Reynolds

I build production websites and data systems solo — infrastructure, application code, analytics, and the per-decision documentation that makes the work readable to someone else six months later.

## Selected work

- **[thailand-livability-index](https://github.com/ReynoldsWJ55/thailand-livability-index)** — public companion repo for the Thailand Liveability Index: methodology, citations, and reproducible build steps.
- **[thailand-canonical-admin-names](https://github.com/ReynoldsWJ55/thailand-canonical-admin-names)** — canonical English and Thai names for Thailand's administrative units at all three levels, with TIS-1099 and ISO 3166-2 codes, an override registry, computed centroids, and bundled polygons. CC BY 4.0.

## What I've shipped

A multilingual consultancy site taken from effectively zero organic presence to position 1 on Google and Bing for branded queries, with sitelinks and AI overviews. Site-wide conversion sits at approximately 15%. ChatGPT referral accounts for roughly 9% of traffic and converts at approximately 58% — the highest of any channel, and the direct result of citation-friendly schema, server-rendered HTML, and explicit Author/Organization markup. Not an accident.

Two findings from the same project: a duplicate-firing analytics event that had inflated conversion totals 2×, caught by reconciling client-side fires against server-side logs; and a deployment-alias canonical conflict resolved at the build-config level, with Search Console validating six pages inside the window.

**[WJR Visuals](https://wjrvisuals.com)** — photography published in The Guardian, U.S. Army, and Photo-Weekly Germany. The portfolio scores 95 mobile / 98 desktop on PageSpeed, all Core Web Vitals green, accessibility 100/100 verified through screen-reader testing. Static Next.js, no server runtime, near-zero operating cost.

## What I'm building now

**[Thailand Liveability Index](https://thailandliveabilityindex.com)** is a 77-province composite index across seven categories, sourced from public datasets and cited APA 7 from day one. The pipeline runs on DuckDB for analysis, Cloudflare Workers + R2 for orchestration and artifact storage, and a manifest-driven ingestion layer that's reproducible end-to-end from raw source. Built solo across data engineering, methodology, geographic coverage, and editorial.

Phase 1 closed April 2026. Phase 2 reached end-to-end production validation in week 1. MVP launch targets late August 2026; first annual report ships December 2026 as a 15–20 page gated PDF. Outputs will be registered with DOI and deposited to Zenodo and SSRN. Journal submission targets 2028–2029, to *Cities*, *Habitat International*, or *Environment and Planning B*.

## How I work

Every locked decision gets a per-decision memo with an explicit state — Locked, Provisional, Superseded. Every data release ships with a reproducibility manifest. Relearning your own choices six months later costs more than writing them down once.

I scope down when the scope is wrong. I check source data before flagging issues — external crawls produce false negatives on server-rendered sites. Defenses go in layers: any single one should fail independently without taking the system with it.

Code style is boring on purpose: type-checked where the type system earns its weight, tested where regressions actually hurt, with CI that gates the things that have broken before rather than the things that look good in a checklist.

## Repositories

Public repos here cover methodology, tooling, and writeup layers. Production data pipelines and client codebases stay private — happy to walk through architecture, trade-offs, and decision memos on request.

## Client work

Four-to-five page performance-grade sites for small businesses: real schema infrastructure, self-hosted analytics with conversion attribution, Core Web Vitals in the 90+ range on actual measurement. The same tools and discipline as everything above.

Best fit: small businesses in North America and Southeast Asia who want a site that ranks and converts. Engagements typically ship in four to six weeks.

## Connect

[developedbywill.com](https://developedbywill.com) — inquiries, project conversations, or to walk through architecture and decision memos.
