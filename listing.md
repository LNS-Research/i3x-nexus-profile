# CESMII Smart Manufacturing Catalog — listing sheet

Fields follow what the Catalog shows on every entry (catalog.cesmii.net/asset/…): name, vendor,
description, tags, SM imperative, category, asset link, vendor website, images.
Everything below is hosted at https://github.com/LNS-Research/i3x-nexus-profile.

---

## Vendor (new)

| Field | Value |
|---|---|
| Name | LNS Research |
| Website | https://www.lnsresearch.com |
| Logo | `images/01-lns-ai-logo.png` (light backgrounds), `images/01b-lns-ai-logo-white.png` (dark) |
| About | LNS Research is an industrial transformation research firm. Its analysts work with manufacturing leaders on operations strategy, industrial AI and the decisions that sit between them. LNS.AI is its applied-AI practice. |

## Asset

| Field | Value |
|---|---|
| Name | i3X Nexus |
| Vendor | LNS Research |
| SM imperative | i3X |
| Category | Product (specification plus reference implementation) |
| Tags | #Server #Governance #Redundancy #AIAgents #Specification |
| Status | Draft 0.4, offered for comment |
| Hero image | `images/02-hero-1600x900.png` |
| Gallery | `images/03-summary-page.png`, `images/04-architecture.png`, `images/05-governed-write.png`, `images/06-proof.png` |
| Documents | `docs/i3X-Nexus-Profile.pdf` (specification), `docs/i3X-Nexus-Summary.pdf` (one page) |

### Description (short — the line under the title)

One i3X endpoint per plant for live values, history, records and media, where every write by a
person, system or AI agent is authorised, recorded, reversible and read back.

### Description (long)

The i3X Nexus is a profile of CESMII i3X 1.0. It defines one endpoint per plant site that serves
live values, history, business records (work orders, quality holds, decision records) and media
(camera video, images, audio) in a single address space.

What it adds is governance for writes. No client writes to a plant or business system directly.
A person or an AI agent submits a write request that records who asked, the decision behind it,
and how to undo it. The site's authority limits decide who must approve; agents may ask but never
approve, and nobody approves their own request. The write is applied only if the target has not
changed since the request, then read back; a mismatch is undone automatically. Every step is a
hash-chained record an auditor can replay. Setpoints carry hard limits on range and step, and
need a named person's approval every time.

It is built to keep running: two nodes with automatic failover, a redundant database with a
three-member quorum, priority lanes that never drop alarms or approvals under load, and a site
that keeps working when its internet link is down.

Everything stays inside the i3X 1.0 contract, so any existing i3X client works unchanged.

**Measured on the reference implementation (synthetic data only):**
- CESMII i3X 1.0 conformance suite: Full 1.0 Compliance, 0 failures, 0 warnings over HTTPS
- The suite still passes with the write node killed mid-run
- 20 forced node kills under write load: writes resume within 12.5 s, 0 lost, 0 duplicated
- Database primary killed: writes resume within 20 s in each direction
- 10,000 fuzzed setpoint values: none outside the declared limits accepted

### Connects to

OPC UA, MQTT and Sparkplug B sources; plant historians (Ignition SQL on PostgreSQL, MySQL or SQL
Server); CMMS/MES records through a REST adapter; OAuth 2 sign-in or client certificates; a
media gateway for live video and audio.

## Public links

| Item | URL |
|---|---|
| Asset link (repository) | https://github.com/LNS-Research/i3x-nexus-profile |
| Vendor logo (light) | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/images/01-lns-ai-logo.png |
| Vendor logo (dark) | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/images/01b-lns-ai-logo-white.png |
| Hero image | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/images/02-hero-1600x900.png |
| One-page summary (image) | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/images/03-summary-page.png |
| Architecture | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/images/04-architecture.png |
| Governed write path | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/images/05-governed-write.png |
| Measured results | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/images/06-proof.png |
| Specification (PDF) | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/docs/i3X-Nexus-Profile.pdf |
| One-page summary (PDF) | https://raw.githubusercontent.com/LNS-Research/i3x-nexus-profile/main/docs/i3X-Nexus-Summary.pdf |
| Conformance evidence | https://github.com/LNS-Research/i3x-nexus-profile/tree/main/evidence |
