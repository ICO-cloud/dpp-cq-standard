**ICO-TS-001:2026**　　　　　　　　　　　　　　July 2026

# DPP-CQ: Digital Product Passport for Cultural & Quality Goods
## Standard Architecture and Core Specifications

### 文化与品质数字产品护照 · 标准架构与核心规范
#### ICO Digital Trust Standards Framework v1.3

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![License: CC BY 4.0](https://img.shields.io/badge/Docs-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Status: Public Review Draft](https://img.shields.io/badge/Status-Public%20Review%20Draft-orange.svg)](#status)
[![Standard: ICO Std 2001](https://img.shields.io/badge/Standard-ICO%20Std%202001-green.svg)](#core-standards)

---

## Overview

The **International Communication Organization (ICO)** is a multi-stakeholder platform developing open, neutral, and inclusive digital trust standards for cultural products, specialty agricultural goods, geographical indications (GIs), and intangible cultural heritage (ICH) products.

Our flagship standard, **DPP-CQ (Digital Product Passport for Cultural & Quality Goods)**, extends the digital product passport paradigm beyond environmental and circular economy data to encompass cultural value, quality attributes, and craft heritage — addressing a significant gap in the global digital trust landscape.

## Status

> ⚠️ **Early Stage — Draft for Public Comment**
>
> All specifications are currently in draft form and subject to revision based on community input. This is an open development process — we invite participation from all stakeholders.

- **White Paper v1.3 (Draft for Comment)**: [white-paper/README.md](white-paper/README.md)
- **DPP-CQ Technical Specification**: In development
- **Reference Implementation**: Targeted for Q4 2026
- **Public Comment Period**: 45 days (July 6 – August 20, 2026) · Accelerated Procedure

## Core Standards

| Standard ID | Title | Status |
|---|---|---|
| **ICO Std 2001** | Digital Product Passport for Cultural & Quality Goods (DPP-CQ) | Draft |
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

- **Standards-based**: Fully aligned with W3C DID Core and Verifiable Credentials
- **Dual verification support**: QR code (low-cost) and NFC (high-security) physical carriers
- **Three-tier verification**: Quick scan → Deep verification → Judicial-grade forensics
- **Privacy by design**: Zero-Knowledge Proofs enable compliance verification without disclosing sensitive data
- **Technology neutral**: Multi-chain hash anchoring, no vendor lock-in
- **Inclusive by default**: Lightweight implementations for low-resource environments

## Why DPP-CQ?

Existing digital product passport frameworks — developed primarily by advanced economies — focus on industrial products and environmental compliance. This leaves significant categories underserved:

- **Cultural products** lack digital mechanisms for provenance and heritage verification
- **Geographical indications** face high counterfeiting costs and cross-border recognition challenges
- **Specialty agricultural goods** struggle to communicate quality differentiation globally
- **Developing economies** are excluded from standard-setting and infrastructure building

DPP-CQ fills this gap by focusing on the *cultural value dimension* and *quality dimension* of digital product passports, while maintaining full interoperability with existing and emerging global standards.

## Getting Involved

### Feedback & Discussion

- **Issues**: Technical questions, bug reports, and feature proposals → [Open an Issue](https://github.com/ICO-cloud/dpp-cq-standard/issues)
- **Email**: Formal inquiries and working group applications → info@icoun.org

### Ways to Participate

| Pathway | Description |
|---|---|
| **Technical Contribution** | Contribute to reference implementations, SDKs, and tools (coming soon) |
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
ico-standards/
├── white-paper/          # White paper (CN + EN)
├── specs/                # Technical specifications
│   ├── dpp-cq/           # DPP-CQ standard
│   ├── did-method/       # DID method specification
│   └── vocabulary/       # JSON-LD context and vocabulary
├── schemas/              # JSON schemas for data models
├── reference/            # Reference implementations (planned)
├── sdk/                  # Language SDKs (planned)
├── governance/           # Governance documents and charters
├── assets/               # Logos, diagrams, and brand assets
├── ROADMAP.md            # Project roadmap
├── CONTRIBUTING.md       # Contribution guidelines
└── LICENSE               # Apache 2.0 (code) / CC BY 4.0 (docs)
```

## License

This repository contains two types of content with different licenses:

- **Specifications, documentation, and white papers**: Creative Commons Attribution 4.0 International ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/))
- **Software, reference implementations, SDKs, and tools**: Apache License, Version 2.0 ([LICENSE](LICENSE))

## Contact

- **Standards inquiries**: info@icoun.org
- **Security reports**: info@icoun.org
- **Partnership**: info@icoun.org
- **Website**: https://icoun.org (forthcoming)

---

*Trust is the most valuable public good in the digital age. We invite you to join us in building a more inclusive digital trust ecosystem — where the unique value of every culture is visible, verifiable, and respected worldwide.*

**International Communication Organization (ICO)**
