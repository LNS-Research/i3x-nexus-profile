# i3X Nexus Profile

A profile of CESMII i3X 1.0 from LNS Research: one governed, redundant i3X endpoint per plant
for live values, history, records and media, where every write by a person, system or AI agent
is authorised, recorded, reversible and read back. Draft 0.4, offered for comment.

This repository holds the specification, a one-page summary, images, and the conformance and
failover evidence from the reference implementation. Everything is product-neutral and was
measured on synthetic data; no customer data appears anywhere.

© LNS Research. All rights reserved. Shared for review and comment.

| Path | What it is |
|---|---|
| `listing.md` | The CESMII Smart Manufacturing Catalog listing in the Catalog's own fields: vendor, asset, short and long description, tags, imperative, images, documents |
| `images/01-lns-ai-logo.png` | LNS.AI logo, for light backgrounds (2154×876) |
| `images/01b-lns-ai-logo-white.png` | LNS.AI logo, for dark backgrounds |
| `images/02-hero-1600x900.png` | Hero card for the asset page |
| `images/03-summary-page.png` | The one-page summary as an image |
| `images/04-architecture.png` | Reference architecture |
| `images/05-governed-write.png` | How a governed change works |
| `images/06-proof.png` | Measured results |
| `docs/i3X-Nexus-Profile.pdf` | The specification, draft 0.4 (also as `.html`) |
| `docs/i3X-Nexus-Summary.pdf` | One-page summary |
| `evidence/https-run.json` | CESMII conformance suite over HTTPS: Full 1.0 Compliance, 0 failures, 0 warnings |
| `evidence/run-{1,2,3}.json` | Three consecutive suite runs with governed writes on |
| `evidence/failover-run.json` | Suite run with the write node killed mid-run |
| `evidence/failover-drill.json` | 20 forced node kills under write load |
| `src/` | HTML sources the images were rendered from (headless Chrome) |
