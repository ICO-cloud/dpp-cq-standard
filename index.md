---
layout: home
title: "DPP-CQ Standard"
---

# DPP-CQ: Digital Product Passport for Cultural & Quality Goods

> **ICO Std 2001:2026** — An open digital trust standard for cultural products, specialty agricultural goods, geographical indications, and intangible cultural heritage.

---

## 📢 Second Public Review — v2.0.0-draft

This standard is currently in **Second Public Review Draft** status (v2.0.0-draft).

- **Comment Period:** September 1 – October 15, 2026
- **Feedback:** [Open an Issue](https://github.com/ICO-cloud/dpp-cq-standard/issues) or email [info@icoun.org](mailto:info@icoun.org)

### What's New in v2.0

| Enhancement | Description |
|---|---|
| **GS1 Digital Link** | Native URI syntax for global carrier interoperability |
| **Three-tier carriers** | L1 (Open QR) → L2 (SDM Secure NFC) → L3 (Tamper-evident NFC) |
| **Dual credential formats** | BBS+ JSON-LD Data Integrity and SD-JWT VC (IETF RFC 9529) |
| **Chinese cryptography** | SM2/SM3/SM4 optional module (GM/T standards) |
| **Sustainability** | ISO 14067 carbon footprint disclosure module |
| **AI transparency** | EU AI Act Art.50 and GB/T 47507-2026 disclosure |
| **Data lifecycle governance** | Privacy impact assessment, cross-border data rules |
| **Governance Charter** | Open multi-stakeholder governance framework (v0.5) |

---

## Overview

DPP-CQ extends the digital product passport paradigm beyond environmental and circular economy data to encompass **cultural value**, **quality attributes**, and **craft heritage** — addressing a significant gap in the global digital trust landscape.

### Key Features

| Feature | Description |
|---------|-------------|
| **Eight Data Modules** | Base Identity (DID), Quality Data, Cultural Data, Geographical Indication, Traceability, Sustainability, Carrier & GS1, Data Lifecycle |
| **Three Physical Carriers** | L1 Open QR · L2 SDM NFC · L3 Tamper-evident NFC |
| **Dual Credential Formats** | BBS+ selective disclosure + SD-JWT VC |
| **Three-Level Verification** | Quick check (<1s) → Deep verification → Judicial-grade forensics |
| **Privacy by Design** | Zero-Knowledge Proofs for compliance without disclosing sensitive data |
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

### Core Documents

| Document | Description | Language |
|----------|-------------|----------|
| [White Paper v2.0](docs/white-paper/white-paper-v2.0.md) | Complete standard specification (ICO Std 2001:2026 v2.0.0-draft) | English |
| [White Paper v2.0 PDF](docs/white-paper/DPP-CQ_White_Paper_v2.0_EN.pdf) | Pure English PDF (with all normative annexes) | English |
| [White Paper v1.3 (English)](docs/white-paper/white-paper-en.md) | Previous version | English |
| [Executive Summary](docs/white-paper/executive-summary.md) | Concise overview for decision-makers | English |
| [Governance Charter v0.5](docs/governance/governance-charter-v0.5.md) | Multi-stakeholder governance framework | English |
| [JSON Schema Reference](schema.html) | Data model specification (v2.0.0-draft) | — |
| [Credential Examples](examples.html) | Sample credential payloads (v1.3 + v2.0) | — |

### Normative Annexes (v2.0)

| Annex | Description |
|-------|-------------|
| [GS1 Digital Link Mapping](docs/interoperability/gs1-digital-link-mapping.md) | GTIN↔DID binding, Digital Link URI, EPCIS 2.0 events |
| [Carrier Specification](docs/interoperability/carrier-specification.md) | L1/L2/L3 carrier definitions, dual-carrier rules, resolver behaviour |
| [Credential Formats](docs/specs/credential-formats.md) | BBS+ and SD-JWT VC format profiles, P/H/R disclosure, crypto suites |
| [Conformity Declarations](docs/compliance/conformity-declarations.md) | Multi-framework compliance statements |
| [PIA Summary](docs/compliance/pia-summary.md) | Privacy impact assessment, data lifecycle, cross-border rules |

### PDF Downloads

- 📄 [White Paper v2.0 (English)](docs/white-paper/DPP-CQ_White_Paper_v2.0_EN.pdf) — includes all normative annexes
- 📄 [White Paper v1.3 (English)](docs/white-paper/DPP-CQ_White_Paper_v1.3_EN.pdf)

---

## Interoperability

DPP-CQ is built **on top of** established international standards:

| Standard | Relationship |
|----------|-------------|
| **W3C DID / VC v2.0** | Core technology foundation, fully compliant |
| **GS1 / EPCIS 2.0 / UNTP** | Digital Link URI mapping, event interoper, multilateral bridging |
| **UNECE DPP Initiative** | Active participant in global interoperability framework |
| **EU DPP / ESPR** | Data mapping for cross-system information sharing |
| **ISO 14067 / 22000 / 26000** | Sustainability, quality and social responsibility alignment |
| **IETF SD-JWT VC** | RFC 9529 credential format |
| **EN 18219 / 18220** | EU digital label and carrier standards alignment |

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
|---------|-------------|
| **Technical Contribution** | Contribute to reference implementations, SDKs, and tools |
| **Standard Development** | Join a Working Group to shape the standards |
| **Ecosystem Partnership** | Become a certified service provider or regional node |
| **Adoption** | Implement ICO standards in your products or organization |
| **Pilot Program** | Participate in early pilot projects (tea, ceramics, haute couture) |

---

## Live Platforms

| Platform | URL | Purpose |
|----------|-----|---------|
| Standard Portal | [dppcq.org](https://dppcq.org) | Official standard documentation |
| ICO Overview | [www.icoun.org/dpp-cq/](https://www.icoun.org/dpp-cq/) | Standard overview at ICO |
| Product Verification | [verify.icoun.org](https://verify.icoun.org) | Consumer-facing NFC/QR verification |
| Certificate Lookup | [verify.icoun.org](https://verify.icoun.org) | Institution certificate verification |
| Reference Implementation | [ico-cloud.github.io/dpp-cq-demo](https://ico-cloud.github.io/dpp-cq-demo/) | Demo application |

---

## License

- **Standards & Documentation:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- **Reference Implementations:** [Apache 2.0](https://github.com/ICO-cloud/dpp-cq-standard/blob/main/LICENSE)

---

## Contact

- **Organization:** [International Communication Organization (ICO)](https://www.icoun.org)
- **Standards inquiries:** info@icoun.org
- **GitHub:** [ICO-cloud/dpp-cq-standard](https://github.com/ICO-cloud/dpp-cq-standard)

---

*Published by the International Communication Organization (ICO) · ICO Std 2001:2026 v2.0.0-draft*
