**ICO Std 2001:2026**             September 2026

# DPP-CQ: Digital Product Passport for Cultural & Quality Goods
## Standard Architecture and Core Specifications

### 文化与品质数字产品护照 · 标准架构与核心规范
#### ICO Digital Trust Standards Framework v2.0

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%2.0-blue.svg)](LICENSE)
[![License: CC BY 4.0](https://img.shields.io/badge/Docs-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Status: Second Public Review](https://img.shields.io/badge/Status-Second%20Public%20Review-orange.svg)](#status)
[![Standard: ICO Std 2001](https://img.shields.io/badge/Standard-ICO%20Std%202001-green.svg)](#core-standards)

---

## Overview

The **International Communication Organization (ICO)** is a multi-stakeholder platform developing open, neutral, and inclusive digital trust standards for cultural products, specialty agricultural goods, geographical indications (GIs), and intangible cultural heritage (ICH) products.

Our flagship standard, **DPP-CQ (Digital Product Passport for Cultural & Quality Goods)**, extends the digital product passport paradigm beyond environmental and circular economy data to encompass cultural value, quality attributes, and craft heritage — addressing a significant gap in the global digital trust landscape.

## Status

> ⚠️ **Second Public Review — v2.0.0-draft**
>
> This is the second public review period for DPP-CQ v2.0.0-draft. The specification has been substantially revised since v1.3, incorporating GS1 Digital Link interoperability, three-tier carrier specification, dual credential formats (BBS+ and SD-JWT VC), Chinese cryptography optional module, and sustainability alignment with ISO 14067.

- **White Paper v2.0 (Second Public Review)**: [docs/white-paper/white-paper-v2.0.md](docs/white-paper/white-paper-v2.0.md)
- **Governance Charter v0.5 (Working Draft)**: [docs/governance/governance-charter-v0.5.md](docs/governance/governance-charter-v0.5.md)
- **Technical Specification v2.0.0-draft**: [dppcq.org/spec/](https://dppcq.org/spec/)
- **Reference Implementation (Demo)**: [ico-cloud.github.io/dpp-cq-demo](https://ico-cloud.github.io/dpp-cq-demo/)
- **Public Comment Period**: Sep 1 – Oct 15, 2026

**Official Standard Portal**: [https://dppcq.org](https://dppcq.org)

## Core Standards

| Standard ID | Title | Status |
|---|---|---|
| **ICO Std 2001** | Digital Product Passport for Cultural & Quality Goods (DPP-CQ) | v2.0 Public Review |
| ICO Std 1001 | Global Information Credibility & Data Traceability Specification | Planned |
| ICO Std 3001 | Global Digital Credibility Certification (GDCC) | Planned |
| ICO Std 2002 | Haute Couture & Cultural Craftsmanship Standard | Planned |
| ICO Std 2003 | GI Cross-Border Mutual Recognition Standard | Planned |

## Architecture

```
┌─────────────────────────────────────────────────────┐
│  Governance & Compliance Layer  (4000-series)       │
│  Standards process · Multi-stakeholder governance   │
│  Dispute resolution · Certification rules           │
├─────────────────────────────────────────────────────┤
│  System & Assessment Layer  (3000-series)           │
│  Institutional credibility · Cross-cultural trust   │
│  AI content traceability · Assessment frameworks    │
├─────────────────────────────────────────────────────┤
│  Product Standards Layer  (2000-series)             │
│  DPP-CQ · GI Mutual Recognition · Haute Couture     │
│  Intangible Cultural Heritage · Specialty Foods     │
├─────────────────────────────────────────────────────┤
│  Base Protocols Layer  (1000-series)                │
│  DID · Verifiable Credentials · Data Traceability   │
│  Naming conventions · Cryptographic suites          │
└─────────────────────────────────────────────────────┘
```

## Key Design Principles

- **Standards-based**: Fully aligned with W3C DID Core and Verifiable Credentials v2.0
- **GS1 interoperable**: Native GS1 Digital Link URI syntax for carrier identification
- **Three-tier carriers**: L1 (Open QR) → L2 (SDM Secure NFC) → L3 (Tamper-evident NFC)
- **Dual credential formats**: BBS+ selective disclosure and SD-JWT VC (IETF RFC 9529)
- **Chinese cryptography optional**: SM2/SM3/SM4 support per GM/T standards
- **Privacy by design**: Zero-Knowledge Proofs enable compliance verification without disclosing sensitive data
- **Sustainability aligned**: ISO 14067 carbon footprint module
- **AI transparency**: EU AI Act Art.50 and GB/T 47507-2026 compliance disclosure
- **Inclusive by default**: Lightweight implementations for low-resource environments

## Why DPP-CQ?

Existing digital product passport frameworks — developed primarily by advanced economies — focus on industrial products and environmental compliance. This leaves significant categories underserved:

- **Cultural products** lack digital mechanisms for provenance and heritage verification
- **Geographical indications** face high counterfeiting costs and cross-border recognition challenges
- **Specialty agricultural goods** struggle to communicate quality differentiation globally
- **Developing economies** are excluded from standard-setting and infrastructure building

DPP-CQ fills this gap by focusing on the *cultural value dimension* and *quality dimension* of digital product passports, while maintaining full interoperability with existing and emerging global standards.

## v2.0 Enhancements (since v1.3)

| Enhancement | Description |
|---|---|
| **GS1 Digital Link** | Native URI syntax for global carrier interoperability |
| **Three-tier carriers** | L1/L2/L3 classification with SDM security and tamper-evidence |
| **SD-JWT VC** | IETF RFC 9529 credential format alongside BBS+ |
| **Chinese crypto** | SM2/SM3/SM4 optional module (GM/T 0009, GM/T 0004, GM/T 0002) |
| **Sustainability** | ISO 14067 carbon footprint disclosure module |
| **AI transparency** | EU AI Act Art.50 and GB/T 47507-2026 disclosure requirements |
| **Governance Charter** | Open multi-stakeholder governance framework (v0.5) |

## Getting Involved

### Feedback & Discussion

- **Issues**: Technical questions, bug reports, and feature proposals → [Open an Issue](https://github.com/ICO-cloud/dpp-cq-standard/issues)
- **Email**: Formal inquiries and working group applications → info@icoun.org
- **Standard Portal**: [https://dppcq.org](https://dppcq.org)

### Ways to Participate

| Pathway | Description |
|---|---|
| **Technical Contribution** | Contribute to reference implementations, SDKs, and tools |
| **Standard Development** | Join a Working Group to shape the standards themselves |
| **Ecosystem Partnership** | Become a certified service provider, regional node, or industry partner |
| **Adoption** | Implement ICO standards in your products or organization |
| **Pilot Program** | Participate in early pilot projects (tea, ceramics, haute couture) |

### Working Groups

- DPP-CQ Technical WG — Core technical specification development
- Governance & Compliance WG — Governance framework and legal alignment
- Interoperability WG — Integration with W3C, GS1, ISO, EU DPP, and UNECE
- Use Cases & Pilots WG — Real-world implementation and case studies

## Repository Structure

```
dpp-cq-standard/
├── _config.yml           # Jekyll configuration for GitHub Pages
├── index.md              # Documentation site homepage
├── schema.md             # JSON Schema reference page
├── examples.md           # Credential examples page
├── docs/
│   ├── white-paper/      # White paper v2.0 (CN + EN) — PDF & Markdown
│   ├── governance/       # Governance Charter and framework documents
│   └── README.md
├── schemas/              # JSON schemas for DPP-CQ data models
├── examples/             # Example DPP-CQ credential payloads
├── .github/              # Issue templates (Bug, Comment, Feature Request)
├── ROADMAP.md            # Project roadmap
├── CHANGELOG.md          # Version history
├── CONTRIBUTING.md       # Contribution guidelines
├── CODE_OF_CONDUCT.md    # Community conduct expectations
├── SECURITY.md           # Security / vulnerability reporting policy
└── LICENSE               # Apache 2.0
```

## License

This repository contains two types of content with different licenses:

- **Specifications, documentation, and white papers**: Creative Commons Attribution 4.0 International ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/))
- **Software, reference implementations, SDKs, and tools**: Apache License, Version 2.0 ([LICENSE](LICENSE))

## Documentation Sites

| Site | URL |
|---|---|
| **Standard Portal** | [https://dppcq.org](https://dppcq.org) |
| **ICO Overview** | [https://www.icoun.org/dpp-cq/](https://www.icoun.org/dpp-cq/) |
| **GitHub Pages** | [https://ico-cloud.github.io/dpp-cq-standard/](https://ico-cloud.github.io/dpp-cq-standard/) |
| **Demo** | [https://ico-cloud.github.io/dpp-cq-demo/](https://ico-cloud.github.io/dpp-cq-demo/) |

## Contact

- **Standards inquiries**: info@icoun.org
- **Security reports**: info@icoun.org
- **Partnership**: info@icoun.org
- **Website**: [https://www.icoun.org](https://www.icoun.org)

---

*Trust is the most valuable public good in the digital age. We invite you to join us in building a more inclusive digital trust ecosystem — where the unique value of every culture is visible, verifiable, and respected worldwide.*

**International Communication Organization (ICO)**
