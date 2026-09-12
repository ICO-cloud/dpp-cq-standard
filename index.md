---
layout: home
title: "DPP-CQ Standard"
---

# DPP-CQ: Digital Product Passport for Cultural & Quality Goods

> **ICO Std 2001-2026** — An open digital trust standard for cultural products, specialty agricultural goods, geographical indications, and intangible cultural heritage.

---

## 📢 Public Review — v2.0.0-draft

The standard is now in its **second Public Review Draft (v2.0.0-draft)**, focused on international interoperability and compliance.

- **What's new in v2.0:** GS1 Digital Link / GTIN interop profile · EN 18220-aligned three-tier carriers on ISO/IEC baselines (QR: 18004/15415; NFC: 14443 Type 4) · SD-JWT VC (RFC 9529) alongside BBS+ · optional SM2/SM3/SM4 regional cryptography · ISO 14067 sustainability module (quality + sustainability dual-dimension) · AI assessment transparency (EU AI Act Art. 50 / ISO/IEC 42001) · open interoperability API aligned with EN 18222 · OID ↔ DID application-layer bridge · data lifecycle governance · UNTP-style conformity claims
- **Second comment period:** September 1 – October 15, 2026
- **Feedback:** [Open an Issue](https://github.com/ICO-cloud/dpp-cq-standard/issues) or email [info@icoun.org](mailto:info@icoun.org)

---

## Overview

DPP-CQ extends the digital product passport paradigm beyond environmental and circular economy data to encompass **cultural value**, **quality attributes**, and **craft heritage** — addressing a significant gap in the global digital trust landscape.

### Key Features

| Feature | Description |
|---------|-------------|
| **Data Modules** | Identity (DID + optional GTIN/GLN), Quality & Assessment, Cultural, Geographical Indication, Traceability (EPCIS-mappable), Sustainability (optional), Data Lifecycle, Credential Proof |
| **Dual Physical Carrier** | QR code (low-cost) + NFC (high-security) |
| **Three-Level Verification** | Quick check (<1s) → Deep verification → Judicial-grade forensics |
| **Privacy by Design** | Selective-disclosure proofs (SD-JWT / BBS+) for compliance without exposing sensitive data |
| **Technology Neutral** | Multi-chain hash anchoring, no vendor lock-in |

### Architecture Layers

| Layer | Series | Scope |
|-------|--------|-------|
| Governance & Compliance | 4000 | Standards process · Multi-stakeholder governance · Dispute resolution |
| System & Assessment | 3000 | Institutional credibility · Cross-cultural trust · AI content traceability |
| Product Standards | 2000 | DPP-CQ · GI Mutual Recognition · Haute Couture · ICH |
| Base Protocols | 1000 | DID · Verifiable Credentials · Data Traceability · Cryptographic suites |

---

## Documentation

| Document | Description | Language |
|----------|-------------|----------|
| [White Paper (中文)](docs/white-paper/) | Complete standard specification (ICO-TS-001:2026 v2.0.0-draft) | 中文 |
| [White Paper (English)](docs/white-paper/white-paper-en.md) | Full English version | English |
| [Executive Summary](docs/white-paper/executive-summary.md) | Concise overview for decision-makers | English |
| [GS1 Digital Link Mapping](docs/interoperability/gs1-digital-link-mapping.md) | GTIN↔DID binding, Digital Link resolution, EPCIS mapping | English |
| [Carrier Specification](docs/interoperability/carrier-specification.md) | Three-tier carriers (QR / SDM NFC / tamper-evident), EN 18220 aligned; ISO/IEC 14443/18004/15415 baselines | English |
| [Identifier Mapping (OID ↔ DID)](docs/interoperability/identifier-mapping.md) | Application-layer OID ↔ DID binding via `alsoKnownAs` / `identifiers.alias` | English |
| [Open Interoperability API](docs/interoperability/api-specification.md) | REST API aligned with EN 18222:2026; Read/Lifecycle/Search conformance | English |
| [Credential Formats](docs/specs/credential-formats.md) | SD-JWT VC (RFC 9529) vs BBS+ profiles; SM2/SM3/SM4 optional regional suite | English |
| [Conformity Declarations](docs/compliance/conformity-declarations.md) | ESPR/EN, ISO/IEC 42001, GDPR/PIPL, AI Act alignment; jurisdiction mappings informative | English |
| [PIA / DPIA Summary](docs/compliance/pia-summary.md) | Public privacy impact assessment summary | English |
| [JSON Schema Reference](schema.html) | Data model specification (v2.0) | — |
| [Credential Examples](examples.html) | Sample credential payloads (v1 & v2.0) | — |

### PDF Downloads

- 📄 White Paper PDFs (v1.3, English/Chinese): being regenerated for v2.0 — the Markdown versions above are the current authoritative text

---

## Interoperability

DPP-CQ is built **on top of** established international standards:

| Standard | Relationship |
|----------|-------------|
| **W3C DID / VC v2.0** | Core technology foundation, fully compliant |
| **IETF SD-JWT (RFC 9529)** | Normative selective-disclosure credential profile |
| **GS1 Digital Link / GTIN / EPCIS 2.0** | Normative interop profile for global retail, customs and EU DPP data exchange |
| **EU ESPR / EN 18216–18223 (incl. EN 18222 APIs)** | Baseline alignment: open carriers, unique identifiers, lifecycle/search APIs, sustainability data fields |
| **UN/CEFACT UNTP** | Conformity claim vocabulary; multilateral bridge |
| **ISO/IEC 14067 / 22000 / 22739 / 42001 / 14443 / 18004 / 15415** | Carbon footprint, food safety, blockchain terminology, AI management, NFC/QR carrier baselines |
| **ITU-T X.660 / ISO/IEC 9834-1; 8824-1; RFC 3061 (OID)** | Application-layer OID ↔ DID bridge; no new DID method |
| **SM2/SM3/SM4 (GB/T 32918/32905/32907)** | Optional regional cryptography suite, opt-in per jurisdiction |

DPP-CQ's flagship categories (tea, wine & spirits, cultural crafts, traditional
medicine products, specialty agri-foods) are not within the first EU ESPR
priority product groups. The strategy is **baseline compatibility with
differentiated value**: full interop on carriers, identifiers and formats,
while keeping the independent quality-and-culture assessment framework.

---

## Governance

ICO employs a **multi-stakeholder governance** model:

- **General Assembly** — Supreme decision-making body, meets annually
- **Standards Council** — 25% government / 25% industry / 20% academia / 20% civil society / 10% Technical Secretariat (non-voting)
- **Technical Secretariat** — Neutral execution body; maintains reference implementations, operates Root Resolver Network
- **Working Groups** — Open participation for all members

---

## How to Participate

| Pathway | Description |
|------