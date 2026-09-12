========================================================================
                    ICO-TS-001                      August 2026

   DPP-CQ: Digital Product Passport for Cultural & Quality Goods
               Standard Architecture and Core Specifications

                    Version 2.0.0-draft — Public Review Draft (2nd round)
========================================================================

  Originating Organization:  International Communication Organization (ICO)
  Document Number:           ICO-TS-001:2026
  Status:                    Public Review Draft
  Comment Period:            September 1 – October 15, 2026 (2nd review: interoperability & compliance)
  Feedback:                  info@icoun.org | GitHub Issues
========================================================================

---

# DPP-CQ: Digital Product Passport for Cultural & Quality Goods
## Standard Architecture and Core Specifications

### DPP-CQ 文化与品质数字产品护照
### 标准架构与核心规范

#### (ICO Digital Trust Standards Framework v2.0.0-draft)
#### （ICO 数字信任标准框架 v2.0.0-draft）

---

## Abstract · 摘要

Against the backdrop of deep integration between the digital economy and global trade, cross-border product circulation is evolving from *physical flow* to *trusted flow*. Digital Product Passports (DPPs), as an emerging digital trust infrastructure, have achieved significant progress in the environmental data domain for industrial products, yet notable gaps remain in their coverage of cultural products, specialty agricultural goods, geographical indication products, and other categories.

This document systematically presents the overall architecture, core specifications, governance mechanisms, and implementation roadmap of the **DPP-CQ Digital Product Passport for Cultural & Quality Goods standards framework**. Built upon mature technologies such as W3C DIDs, Verifiable Credentials (VCs), and standards-based selective disclosure (SD-JWT / BBS+), this framework focuses on establishing digital trust in the cultural value and quality dimensions, addressing the inclusivity gap in existing DPP standards ecosystems.

The core standard, **ICO Std 2001 (DPP-CQ)**, is a digital passport specification for cultural and quality products. It supports dual carriers of QR codes and NFC, provides a three-tier verification mechanism, and protects sensitive craftsmanship and commercial data through selective-disclosure proofs (SD-JWT / BBS+). The standards framework employs a multi-stakeholder governance model to ensure openness, neutrality, and inclusivity.

This document is issued as a Public Review Draft. We sincerely invite governments, enterprises, academic institutions, and non-governmental organizations worldwide to participate in building a more inclusive global digital trust ecosystem.

**v2.0.0-draft update (Aug–Sep 2026):** Following the first public review, this revision substantially expands the standard's international interoperability and compliance posture: a GS1 Digital Link / GTIN interop profile, three-tier physical carrier specification (open QR + SDM NFC + tamper-evident NFC) aligned with EN 18220 and normatively referencing ISO/IEC baselines (QR: ISO/IEC 18004 + ISO/IEC 15415; NFC: ISO/IEC 14443 Type 4), two normative credential format profiles (W3C Data Integrity with BBS+ and IETF SD-JWT VC / RFC 9529), an optional regional cryptography suite (SM2/SM3/SM4, opt-in), an ISO 14067-aligned sustainability data module (quality + sustainability dual-dimension model), AI-assisted assessment transparency provisions aligned with EU AI Act Art. 50 and ISO/IEC 42001:2023, an open interoperability API aligned with EN 18222:2026, an OID ↔ DID application-layer identifier bridge (ISO/IEC 9834-1/8824-1 and W3C), data lifecycle governance metadata, and UNTP-style conformity claims. All v2.0 additions are backward compatible with v1.x credentials.

**Keywords**: Digital Product Passport; Cross-Cultural Digital Trust; Quality Assets; DPP-CQ; Decentralized Identifiers; Verifiable Credentials; Selective Disclosure (SD-JWT / BBS+); GS1 Digital Link; Multi-Stakeholder Governance

---

## Scope · 范围

This document describes the **overall architecture, core specifications, governance mechanisms, and implementation roadmap** of the **DPP-CQ Digital Product Passport for Cultural & Quality Goods standards framework**, with particular focus on the technical framework and application model of the core product-level standard **ICO Std 2001-2026 (DPP-CQ)**.

**Applicability:**
- Categories with cultural value and quality attributes, including cultural products, Intangible Cultural Heritage-related products, Geographical Indication (GI) products, specialty agricultural goods, and haute couture products
- Application scenarios including product identity verification, quality grading, traceability verification, and digital confirmation of cultural value
- Technical integration and system interoperability for all participating parties, including producers, certification bodies, trading platforms, and consumers

**Exclusions:**
- Highly regulated special categories such as pharmaceuticals and medical devices (which must comply with sector-specific regulatory requirements)
- High-sensitivity scenarios at the financial-grade or personal safety level, such as financial payment and identity authentication
- Replacement of mandatory compliance requirements such as statutory product safety and quality inspection in respective jurisdictions

---

## Purpose · 目的

This document aims to:
1. Systematically present the design philosophy and overall architecture of the ICO standards framework, providing a panoramic understanding for all stakeholders;
2. Define the core technical specifications and interoperability requirements of the DPP-CQ standard, guiding technical implementation;
3. Describe the governance mechanisms and participation pathways of the standards framework, inviting global stakeholders to co-build;
4. Solicit feedback from all sectors of society to promote continuous improvement and widespread adoption of the standards.

---

## Status of This Document · 本文档状态

This document is a **Public Review Draft** published by the International Communication Organization (ICO).

The content of this document may be revised based on community feedback. The official version shall be as officially published by ICO. This v2.0.0-draft incorporates the results of the first public review (July 6 – August 20, 2026) and opens a **second review period: September 1 – October 15, 2026**, focused on the new international interoperability and compliance annexes. Feedback may be submitted through the following channels:

- GitHub Issues: https://github.com/ICO-cloud/dpp-cq-standard/issues
- Email: info@icoun.org

This document does not constitute a legally binding instrument, nor does it represent the official position of ICO members. Formal publication of the standard requires approval by the ICO Standards Council.

---

## Copyright Notice · 版权声明

© 2026 International Communication Organization (ICO). All rights reserved.

This document and associated standards are published under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**. You are free to share, adapt, and use this work for commercial purposes, subject to the following conditions:
- **Attribution**: You must give appropriate credit, provide a link to the license, and indicate if changes were made.
- **No additional restrictions**: You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

Reference implementations and software source code are released under the **Apache License 2.0** open-source license.

---

## Editors and Contributors · 编辑与贡献者

**Technical Editor:** ICO Technical Secretariat
**Standards Working Groups:** DPP-CQ Technical Working Group, Governance & Compliance Model Group, Interoperability Working Group

**Contributing Organizations (in alphabetical order):**
- International Communication Organization (ICO)
- 天机可信价值研究院 (Tianji Credibility Research Institute)
- (Additional organizations to be added)

For the complete list of contributors and detailed revision history, please refer to the commit history of the GitHub repository.

---

## Revision History · 修订历史

| Version | Date       | Description of Changes                                                                                                                          |
|---------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| v2.0.0-draft | Sep 2026 | International alignment refinement: open interoperability API aligned with EN 18222:2026 (Read/Lifecycle/Search conformance); OID ↔ DID application-layer identifier bridge (X.660/9834-1, 8824-1, RFC 3061, W3C `alsoKnownAs`); carriers normatively reference ISO/IEC 14443 Type 4, ISO/IEC 18004, ISO/IEC 15415; AI provisions aligned with EU AI Act Art. 50 and ISO/IEC 42001:2023; two normative annexes added (api-specification, identifier-mapping) |
| v2.0.0-draft | Aug 2026 | International interoperability & compliance expansion: GS1 Digital Link/GTIN interop profile; three-tier carrier specification (EN 18220 aligned); SD-JWT VC (RFC 9529) profile alongside BBS+; optional SM2/SM3/SM4 regional cryptography suite (opt-in); ISO 14067 sustainability data module (quality+sustainability dual-dimension); AI-assisted assessment transparency (EU AI Act Art. 50); data lifecycle governance metadata; UNTP-style conformity claims; conformity declarations and PIA summary published; all additions backward compatible with v1.x |
| v1.3    | July 2026  | Format standardization: aligned with international technical specification formats; added abstract, document status, copyright notice, and revision history; annexes classified as normative/informative; unified section numbering; main title updated to DPP-CQ; verified accuracy of data citations |
| v1.2    | July 2026  | Added compliance and legal framework chapter, DPP-CQ technical specification annex, intellectual property policy, standards version management strategy, and FAQ; strengthened references to UNESCO/WIPO/UNECE |
| v1.1    | July 2026  | Framework restructuring and refinement: optimized architecture description; added risks and challenges chapter, pilot framework, and UNECE interoperability initiative references |
| v1.0    | July 2026  | First public release (Public Review Draft)                                                                                                      |
| v0.9    | July 2026  | Internal working draft                                                                                                                          |

---

## Table of Contents · 目录

1. [Introduction](#1-introduction)
2. [Mission & Vision](#2-mission--vision)
3. [Background & Rationale](#3-background--rationale)
4. [Standards Architecture](#4-standards-architecture)
5. [Core Standards](#5-core-standards)
6. [Governance](#6-governance)
7. [Technical Approach](#7-technical-approach)
8. [Compliance & Legal Framework](#8-compliance--legal-framework)
9. [Getting Involved](#9-getting-involved)
10. [Roadmap & Pilots](#10-roadmap--pilots)
11. [Risks & Challenges](#11-risks--challenges)
12. [Conclusion](#12-conclusion)
13. [Annex A (Normative): DPP-CQ Technical Specification Draft](#annex-a-normative-dpp-cq-technical-specification-draft)
14. [Annex B (Informative): Glossary](#annex-b-informative-glossary)
15. [Annex C (Informative): Abbreviations](#annex-c-informative-abbreviations)
16. [Annex D (Informative): References](#annex-d-informative-references)
17. [Annex E (Informative): Frequently Asked Questions](#annex-e-informative-frequently-asked-questions)
18. [Annex F (Normative): v2.0 Interoperability & Compliance Annexes](#annex-f-normative-v20-interoperability--compliance-annexes)

---

## 1. Introduction · 前言

In an era of deep integration between the digital economy and global trade, cross-border product circulation is transitioning from *physical flow* to *trusted flow*. However, significant **inclusivity gaps** exist in the current global digital product verification ecosystem:

- Existing Digital Product Passport (DPP) standards primarily focus on environmental and circular economy data for industrial products, and do not adequately cover categories such as cultural products, specialty agricultural goods, and geographical indication products.
- A vast number of products with unique cultural value and quality advantages lack digital trust-transmission tools, making it difficult for them to fully realize their value in global markets. According to a joint OECD/EUIPO study, global trade in counterfeit goods reached USD 467 billion in 2021, accounting for 2.3% of global imports. Among these, geographical indication products and specialty cultural products, with their high recognizability and premium pricing potential, have become prime targets for counterfeiting. Specialty products from developing countries are severely undervalued due to lack of trust.
- Developing economies face multiple challenges in digital trust infrastructure development, including technological, standardization, and capacity gaps. The UN *Global Digital Compact* (GDC) explicitly calls for increased support for digital capacity building in developing countries to ensure that digital technologies benefit all people.

The International Communication Organization (ICO), as a multi-stakeholder international cooperation platform, is committed to advancing **Global Digital Inclusion** and **Cross-Cultural Digital Trust**. This document presents the overall architecture, core standards, governance mechanisms, and implementation roadmap of the ICO standards framework, and invites global stakeholders to join us in building a more inclusive global digital trust ecosystem.

---

## 2. Mission & Vision · 使命与愿景

### 2.1 Mission

**To empower the digital preservation and value transmission of global cultural and quality assets through open standards.**

**以开放标准赋能全球文化与品质资产的数字化保护与价值传递。**

### 2.2 Vision

To build a **globally applicable, technology-neutral, and culturally inclusive** digital trust standards framework, ensuring that every product carrying cultural value and quality commitment possesses a verifiable, traceable, and mutually recognizable digital identity. By 2030, achieve 100,000+ cultural and quality products with globally mutually recognizable digital identities, driving global trade from *price competition* to *value competition*.

### 2.3 Core Principles

| Principle | Description | Practical Manifestation |
|---|---|---|
| **Open** | Standards are open to all stakeholders, regardless of country, region, or ownership structure | Free adoption with no membership fee barriers |
| **Neutral** | Technology-agnostic architecture, not tied to any specific vendor or technology stack | Supports multiple blockchain and cloud platforms |
| **Inclusive** | Fully considers the needs of different cultural backgrounds and development stages | Supports lightweight implementations for low-resource environments |
| **Interoperable** | Based on international technical standards, ensuring connectivity with existing and future systems | Compatible with W3C, ISO, GS1, UNECE, and other standards |
| **Trustworthy** | Verifiable data, traceable processes, and adjudicatable disputes | Three-tier verification + Root Resolver Network + selective-disclosure privacy protection |
| **Privacy by Design** | Privacy protection embedded in architectural design; data minimization | Selective disclosure (SD-JWT / BBS+) |

---

## 3. Background & Rationale · 背景与必要性

### 3.1 The Trust Deficit in Global Trade

In current cross-border global trade, categories such as specialty agricultural goods, cultural products, and handicrafts face pervasive trust challenges: consumers struggle to verify the true origin, quality grade, and cultural background of products; purchasers lack efficient and reliable supply chain traceability tools; authentication of geographical indication products is costly; and cultural value and craft heritage cannot be effectively transmitted through traditional channels.

A direct consequence of this trust deficit is the "bad money drives out good money" effect — genuinely superior products and producers who uphold traditional craftsmanship are unable to obtain returns commensurate with their value in the global market.

### 3.2 Coverage Gaps in Existing Standards

Existing DPP standards are primarily led by advanced economies, focusing on environmental footprints and circular economy data for industrial products, compliance-driven mandatory information disclosure, and serving the market access requirements of developed economies. Significant standard gaps remain in the following areas:

| Gap Area | Current State | ICO Positioning |
|---|---|---|
| Digital confirmation of cultural product rights | No unified cultural value data standard | Establish cultural data models and verification specifications |
| Cross-border mutual recognition of Geographical Indications | WIPO has legal framework but no technical standards | Develop GI digital mutual recognition technical specifications |
| Quality grading for specialty agricultural goods | Individual national standards, no global unified digital framework | Establish cross-cultural quality assessment methodology |
| Digital capacity in developing economies | High technical barriers, high costs, low participation | Provide lightweight, low-threshold solutions |

### 3.3 Interoperability with Existing Standards

ICO standards adopt a strategy of **"baseline compatibility, differentiated value"**:

- **W3C DID/VC**: Used as the underlying identity and credential technology foundation, fully compatible; v2.0 supports both Data Integrity proofs (BBS+) and SD-JWT VC (RFC 9529)
- **GS1 Identification System**: GTIN/GLN identifiers and GS1 Digital Link resolution are supported through a normative interop profile; supply-chain events map to EPCIS 2.0/CBV 2.0; DID and GTIN are bound as complementary identifiers
- **EU DPP / ESPR / EN 18216–18223**: Open data carriers (EN 18220), unique identifiers (EN 18219), data exchange (EN 18216), lifecycle/searchability APIs (EN 18222) and sustainability data attributes are aligned at field level; conformity claims use UNTP-style vocabulary
- **UN/CEFACT UNTP**: Conformity claim and interoperability vocabulary adopted as the multilateral bridge for cross-regime data exchange
- **ISO/ITU-T standards**: ISO 22000 (food safety), ISO 14067 (product carbon footprint), ISO 26000 (social responsibility), ISO 22739 (blockchain terminology), ISO/IEC 14443 (NFC physical/link layer), ISO/IEC 18004/15415 (QR symbology and print quality), ISO/IEC 42001 (AI management system); ISO/ITU-T OID bridged via the application-layer OID ↔ DID binding (see §7.10)
- **Regional cryptographic option**: the SM2/SM3/SM4 commercial cryptography suite is an opt-in profile for deployments within jurisdictions that require it, alongside the default international suites

DPP-CQ does not replace statutory conformity assessment or sectoral certification held by producers; it carries and references such attestations in a verifiable, machine-readable form.

### 3.4 Technology Maturity Window

Technologies such as W3C DIDs (Decentralized Identifiers), Verifiable Credentials, blockchain-based evidence anchoring, and selective-disclosure credential technology (SD-JWT, BBS+) have entered mature application phases, providing the technical foundation for building a globally applicable open standard for the cultural and quality dimensions.

Meanwhile, international documents and data such as UNESCO's *Operational Directives for the Implementation of the Convention for the Safeguarding of the Intangible Cultural Heritage* (2016/2018 edition) and WIPO's *World Intellectual Property Indicators 2024* all indicate the urgency and necessity of leveraging digital technology to protect cultural assets and geographical indications. The timing is opportune for establishing open standards oriented toward the cultural and quality dimensions.

---

## 4. Standards Architecture · 标准体系架构

### 4.1 Four-Layer Architecture

```
┌─────────────────────────────────────────────────────┐
│ Layer 4  Governance & Compliance                     │
│  Standards development process · Multi-stakeholder   │
│  governance · Dispute resolution · Assessment rules │
│  rules                                               │
├─────────────────────────────────────────────────────┤
│ Layer 3  System & Assessment                        │
│  Institutional credibility assessment · Cross-       │
│  cultural trust framework · AI content provenance    │
├─────────────────────────────────────────────────────┤
│ Layer 2  Product Standards                          │
│  Cultural & Quality DPP · Haute couture · GI mutual  │
│  recognition · ICH craftsmanship                     │
├─────────────────────────────────────────────────────┤
│ Layer 1  Base Protocols                             │
│  Digital identifiers · Data provenance · Credential  │
│  formats · Naming conventions                        │
└─────────────────────────────────────────────────────┘
```

### 4.2 Standards Numbering System

| Series | Layer | Positioning | Number Range |
|---|---|---|---|
| **1000 Series** | Base Protocols Layer | Underlying technical specifications, common foundation for all upper-layer standards | 1001–1099 |
| **2000 Series** | Product Standards Layer | Specific data standards and verification specifications for different product categories | 2001–2099 |
| **3000 Series** | System & Assessment Layer | Standards at the institutional assessment, trust system, and methodology level | 3001–3099 |
| **4000 Series** | Governance & Compliance Layer | Standards development processes, governance rules, dispute resolution mechanisms | 4001–4099 |

### 4.3 Initial Core Standards Inventory

| Standard Number | Standard Name | Status | Expected Publication |
|---|---|---|---|
| ICO Std 1001-2026 | Global Information Integrity & Data Provenance | Draft | 2026 Q3 |
| ICO Std 1002-2026 | Digital Credential Format Specification | Under Development | 2026 Q3 |
| **ICO Std 2001-2026** | **Digital Product Passport for Cultural & Quality Goods (DPP-CQ)** | **Public Review Draft** | **2026 Q3** |
| ICO Std 2002-2026 | Global Haute Couture & Cultural Attire Quality Standard | Planned | 2026 Q4 |
| ICO Std 2003-2026 | Global Framework for GI & Origin Digital Mutual Recognition | Planned | 2027 Q1 |
| ICO Std 3001-2026 | Global Digital Credibility Assessment (GDCC) | Draft | 2026 Q4 |
| ICO Std 4001-2026 | Standards Development & Publication Process | Under Development | 2026 Q3 |
| ICO Std 4002-2026 | Multi-Stakeholder Governance Charter | Under Development | 2026 Q3 |

---

## 5. Core Standards · 核心标准介绍

### 5.1 ICO Std 2001: Digital Product Passport for Cultural & Quality Goods (DPP-CQ)

**Positioning:** A digital identity standard for cultural products, specialty agricultural goods, geographical indication products, and ICH handicrafts, providing a unique, trustworthy, and verifiable digital identity credential for every product carrying cultural value and quality commitment.

**Core Data Dimensions:**

| Data Module | Core Fields | Required/Optional |
|---|---|---|
| **Base Identity** | Product unique identifier (DID), issuer information, validity period, category | Required |
| **Quality Data** | Quality grade, test report summary, certification credentials, batch information | Category-required |
| **Cultural Data** | Cultural background, craft heritage, ICH level, artisan/transmitter information | Category-required |
| **Geographical Indication** | Origin, GI certification number, production region data | Required for GI products |
| **Traceability Data** | Full lifecycle event records (production/processing/testing/distribution) | Optional |
| **Credential Data** | Verifiable credential metadata, signatures, revocation status | Required |

**Technical Features:**

- Based on W3C DID Core and Verifiable Credentials international standards
- Supports dual-carrier verification via QR code and NFC
- Three-tier verification mechanism: Quick Verification (<1s) / Deep Verification / Judicial-Grade Verification
- Hybrid storage architecture: data stored off-chain, hashes anchored on-chain
- **ZKP-enabled Privacy:** The standard enables manufacturers, ICH transmitters, and distribution entities to prove compliance with specific quality grades and origin regulatory requirements to consumers and regulatory authorities through selective-disclosure proofs (SD-JWT / BBS+), without disclosing core craft recipes, supply chain node identities, or commercial procurement prices — achieving "data usability without visibility, trustworthiness without information leakage"
- Selective Disclosure: Data holders may choose the scope of disclosure based on the verification scenario

**Applicable Categories:** Geographical indication agricultural products (tea, grains & oils, fruits, medicinal herbs, spices), Intangible Cultural Heritage products (ceramics, embroidery, lacquerware, woodwork), haute couture and cultural attire, premium food and beverages, handicrafts and cultural creative products.

### 5.2 ICO Std 1001: Global Information Integrity & Data Provenance

Defines the credibility assessment framework and provenance methodology for digital content and data assets, with particular emphasis on provenance identification specifications for AI-generated content. Covers data integrity verification, provenance chain construction methods, credibility grading assessment, timestamps, and evidence anchoring interfaces.

### 5.3 ICO Std 3001: Global Digital Credibility Assessment (GDCC)

A digital credibility assessment and evaluation standard for institutions (enterprises, media, NGOs, etc.), constructing an assessment system across multiple dimensions including information transparency, data credibility, governance compliance, and cultural responsibility, with support for cross-cultural scenario adaptation.

---

## 6. Governance · 治理架构

### 6.1 Multi-Stakeholder Governance Model

The ICO standards framework employs a multi-stakeholder governance model to ensure the openness, representativeness, and credibility of standards. Important decisions follow a consensus-first principle; where consensus cannot be reached, decisions are adopted by a two-thirds majority.

Governance design references best practices from international standards bodies such as W3C and IETF, ensuring:
- Balanced representation of economies at different development stages
- Diverse participation from government, industry, academia, and civil society
- Effective separation of technical decision-making from commercial interests

### 6.2 Governance Structure

**General Assembly** (supreme decision-making body): Convened annually to deliberate on strategic direction, budget, and Council elections.

**Standards Council** (decision-making body): Responsible for strategic decisions, standard approval, budget approval, and final dispute adjudication. Seats are allocated by category: Government Representatives 25% / Industry 25% / Academia 20% / Civil Society 20% / Technical Secretariat 10% (non-voting).

**Specialized Committees:**
- Technical Committee: Responsible for standard technical review and technical roadmap planning
- Strategy Committee: Responsible for strategic planning and external cooperation
- Compliance & Dispute Committee: Responsible for compliance review and dispute adjudication

**Standards Working Groups:**
- WG-DPP: Digital Product Passport Working Group
- WG-GI: Geographical Indication Mutual Recognition Working Group
- WG-DID: Decentralized Identifiers and Credentials Working Group
- WG-GDCC: Institutional Credibility Assessment Working Group
- WG-Governance: Governance Rules Working Group

### 6.3 Technical Secretariat

The Technical Secretariat is the neutral executive body of the standards framework, undertaken by a designated entity authorized by the Standards Council. Its core responsibilities:
- Maintain reference implementations and open-source code repositories for the standards
- Provide technical support and conformance testing platforms
- Operate the root resolution infrastructure and trusted registries
- Support the technical work of working groups
- Organize technical training and developer community building

**Key Principle: The Technical Secretariat does not participate in standard voting, ensuring the separation of technical execution from standards development.**

### 6.4 Infrastructure and Root Resolution Mechanism

To ensure high security and continuous availability of data resolution in global cross-border circulation, the ICO Council authorizes the Technical Secretariat to build and operate:

- **ICO Root Resolver Network**: A globally distributed DID resolution infrastructure providing highly available, low-latency identifier resolution and credential status query services
- **Tianji Credibility Registry (TCR)**: A unified credential hash registration and anchoring database

**Operating Mechanism:** When any third-party certification body or service provider issues Digital Product Passports under ICO Std 2001/2003, the credential hash fingerprints and identifiers (DIDs) generated must be registered and consensus-anchored at the root nodes, ensuring traceability and judicial-grade authenticity verification across networks and geographical regions worldwide.

**Security Assurance:**
- Multi-region redundant deployment with 99.99% availability target
- At least one independent third-party security audit per year, with audit reports made public
- Major technical upgrades require review by the Technical Committee and approval by the Standards Council

---

## 7. Technical Approach · 技术路线

### 7.1 Technology Selection Principles

- **International Standards First**: Prioritize adoption of published international standards (W3C, IETF, ISO)
- **Open Source & Open**: Core technology stack based on open-source licenses
- **Extensible Architecture**: Modular design supporting future standard extensions
- **Privacy by Design**: Data minimization principle, implemented via standards-based selective disclosure (SD-JWT / BBS+)

### 7.2 Core Technology Stack

| Layer | Technical Standard | Reference / Compatible Specification |
|---|---|---|
| **Decentralized Identifiers** | W3C DID Core 1.0 | W3C Recommendation (Jul 2022) |
| **Identifier Compatibility** | OID ↔ DID application-layer binding | ITU-T X.660 / ISO/IEC 9834-1; ISO/IEC 8824-1; RFC 3061 |
| **Verifiable Credentials** | W3C Verifiable Credentials Data Model v2.0 | W3C Recommendation |
| **Selective Disclosure** | SD-JWT (RFC 9529) / BBS+ signatures | IETF RFC 9529; W3C Data Integrity BBS cryptosuite |
| **Data Semantics** | JSON-LD 1.1 | W3C Recommendation / IETF BCP 19 |
| **Cryptographic Signatures** | BBS+ / Ed25519 / ECDSA P-256; SM2+SM3 optional | IETF RFC 8032; GB/T 32918 / GB/T 32905 (national crypto option) |
| **Global Product Identification** | GS1 GTIN / GLN / GS1 Digital Link 1.6 | GS1 General Specifications; EU DPP EN 18219 alignment |
| **Supply Chain Events** | GS1 EPCIS 2.0 / CBV 2.0 | GS1 Standard (2022); mapping profile defined in v2.0 |
| **Data Anchoring** | Cryptographic Hash Anchoring | Blockchain-agnostic, multi-chain support |
| **Physical Verification** | QR ISO/IEC 18004 + ISO/IEC 15415 print quality; NFC ISO/IEC 14443 Type 4 with SDM (NTAG 424 DNA class); NFC Forum NDEF | EN 18220:2026 alignment; ISO/IEC baselines |
| **Sustainability Data** | Product carbon footprint per ISO 14067 | Optional sustainability module; ESPR data-attribute direction |
| **Interface Specification** | RESTful API / OpenAPI 3.0; open interop API; Digital Link content negotiation | EN 18222:2026 alignment; OpenAPI Initiative; GS1 Digital Link resolver pattern |

### 7.3 Multi-Chain and Multi-Cloud Architecture

ICO standards are not bound to any specific blockchain or cloud platform. Through a unified hash anchoring abstraction layer, multiple underlying storage solutions are supported (public chains, consortium chains, distributed hash tables, trusted cloud storage, etc.). Different jurisdictions may select anchoring solutions compliant with local regulations while maintaining cross-chain verification consistency.

### 7.4 Open Source Strategy

| Component | Open Source License | Description |
|---|---|---|
| Standards documentation | CC BY 4.0 | Free to use, reproduce, and adapt; attribution required |
| Base protocol reference implementations | Apache 2.0 | Fully open, business-friendly |
| SDKs and development tools | Apache 2.0 | Multi-language SDKs, encouraging ecosystem participation |
| Contribution mechanism | CLA | Contributor License Agreement ensuring clear intellectual property rights |

### 7.5 Intellectual Property Policy

The ICO standards framework adopts an intellectual property policy of "openness first, reasonable protection":

**Standard-Essential Patent (SEP) Policy:**
- Encourages patent holders to license their essential patents on FRAND (Fair, Reasonable, and Non-Discriminatory) terms
- Core standards (DIDs, credential formats, and other base layers) prioritize open-source technology solutions free of patent encumbrances
- Patent searches and disclosures are conducted prior to standard publication to minimize potential patent risks
- An Intellectual Property Working Group is established to oversee patent policy development and dispute resolution

**Trademark and Logo Policy:**
- "ICO Verified" mark, "DPP-CQ" mark, and others are registered trademarks of ICO
- Products and services meeting DPP-CQ conformance requirements may use official marks subject to compliance requirements; DPP-CQ conformance is an assessment/verification (评定/验证), not statutory certification (认证)
- Logo usage specifications and supervision mechanisms are established to prevent abuse and misleading
- Logo usage by regional nodes and partners requires authorization and review

**Copyright Policy:**
- Copyright in standard texts is held by ICO and made available under the CC BY 4.0 license
- Copyright in reference implementations and tool code is held by contributors and open-sourced under the Apache 2.0 license
- Third-party derivative works must comply with the corresponding open-source licenses and indicate source

### 7.6 Standards Version Management

**Version Numbering Scheme:** Uses the format "major.minor.patch" (e.g., v1.2.3)
- **Major version**: Architectural expansion of the standard's scope (e.g. v2.0 adds the GS1 interop profile, SD-JWT VC format and sustainability module); all v2.0 data additions are OPTIONAL so v1.x credentials remain valid
- **Minor version**: Backward-compatible functional additions within the same architecture
- **Patch version**: Backward-compatible bug fixes

**Backward Compatibility Commitments:**
- Minor version updates maintain backward compatibility of data formats and interfaces
- Major version updates provide at least 12 months of transition period and migration tools
- The validity of issued credentials is not affected by standard version updates

**Standards Lifecycle:**
- Working Draft (WD) → Committee Draft (CD) → Public Review Draft (PR) → International Standard (IS)
- International standards are reviewed every 5 years to ensure continued validity
- Obsolete standards initiate revocation procedures with advance notice to all adopters

### 7.7 Physical Carrier Strategy: Three-Tier, Open by Default

DPP-CQ v2.0 defines three physical carrier levels (normative detail: [Carrier Specification](../interoperability/carrier-specification.md)):

| Level | Carrier | International baseline | Security profile | Reader requirement |
|---|---|---|---|---|
| L1 | Open QR (GS1 Digital Link in interop profile) | ISO/IEC 18004 (QR symbology); ISO/IEC 15415 (print quality) | Cloneable; authenticity via registry | Any smartphone camera |
| L2 | SDM secure NFC (NTAG 424 DNA class) | ISO/IEC 14443 Type 4; NFC Forum NDEF | Per-scan cryptographic SUN authentication | Any NFC phone, NDEF open read |
| L3 | Tamper-evident NFC (TagTamper class) | ISO/IEC 14443 Type 4; NFC Forum NDEF | Tamper detection + SDM | Any NFC phone |

Two principles govern carrier design:

1. **Open carrier principle (aligned with ESPR Art. 9 and EN 18220:2026):**
   every product must be readable with generally available means — no
   proprietary app, registration, or fee. QR symbology follows ISO/IEC 18004
   and print quality follows ISO/IEC 15415; NFC follows ISO/IEC 14443 Type 4
   with open NFC Forum NDEF records. Security is achieved through cryptographic
   verification of the resolved data, never through hiding the payload.
2. **Dual carrier for international products:** products in the GS1 interop
   profile carry both an open QR (universal scanning, retail/customer flows)
   and an SDM NFC tag (cryptographic authenticity); both resolve to the same
   passport, and the verification page indicates which carrier was presented.

### 7.8 Dual-Dimension Data Model: Quality + Sustainability

Existing DPP regimes (notably the EU ESPR framework) organize product data
primarily around environmental sustainability and circular economy. DPP-CQ's
core differentiation is the **quality and cultural value** dimension. v2.0
formalizes a dual-dimension model rather than choosing between them:

- **Quality & cultural dimension (DPP-CQ core):** quality grade, sensory and
  laboratory attributes, craftsmanship, ICH/GI status, artisan lineage,
  assessment methodology and AI-use disclosure.
- **Sustainability dimension (v2.0 optional module):** product carbon footprint
  per ISO 14067, material composition with recycled content, end-of-life
  guidance — structured to map onto ESPR delegated-act data attributes as they
  are adopted per product class.

This design lets a single credential serve both purposes: it satisfies the
cultural/quality trust gap DPP-CQ was created to address, while producing
machine-readable sustainability data that EU importers, retailers and
regulators can consume. The quality assessment itself remains governed by ICO
standards (notably Std 3001), preserving the framework's independence.

### 7.9 AI-Assisted Assessment Transparency

Where AI systems support quality assessment (data extraction, pre-scoring,
image recognition), DPP-CQ adopts its own transparency and human-oversight
rules, aligned with the transparency obligations of **EU AI Act Art. 50** and
the governance direction of **ISO/IEC 42001:2023 (AI management system,
AIMS)**:

- AI participation **MUST** be disclosed in the credential
  (`qualityAttributes.assessment.aiDisclosure`).
- The final grading decision **MUST** be made by a qualified human assessor;
  the credential identifies the decision role and review process.
- The assessment methodology reference and full report **MUST** be
  retrievable via the credential (`reportReference`).

### 7.10 Identifier Interoperability: OID ↔ DID Bridge Between Two International Systems

The canonical identifier of a DPP-CQ credential is the W3C DID
(`did:ico:dpp`). So that a credential can also be resolved by certificate,
enterprise-registry and trade/customs systems built on the ISO/IEC & ITU-T
Object Identifier (OID) architecture, v2.0 defines an **application-layer**
OID ↔ DID compatibility binding — not a new DID method and not a change to
root resolution. Normative detail is in
[identifier-mapping.md](../interoperability/identifier-mapping.md); key points:

- **Two complementary international systems:** OID (registration tree per
  ITU-T X.660 / ISO/IEC 9834-1; ASN.1 OBJECT IDENTIFIER and OID-IRI per
  ISO/IEC 8824-1) carries organizational/registration lineage; the W3C DID
  carries cryptographic control proof and verifiability.
- **Binding (normative):** the DID document lists the equivalent OID via the
  standard W3C `alsoKnownAs` property (in RFC 3061 `urn:oid:` form), and the
  credential carries the same equivalence in `identifiers.alias`; the OID-side
  record may point back to the passport URI. No new `did:oid:` method is
  registered.
- **Bidirectional agreement required:** the DID document and credential
  record must cite the same OID, and that OID must be formally allocated by an
  X.660 / 9834-1 Registration Authority. A one-sided claim, an unallocated
  OID, or a mismatch is surfaced as an identifier-consistency warning. ICO
  does not allocate OID arcs.
- **Optional, non-disruptive:** issuers not using OID rely on the canonical
  DID path alone; the binding does not alter hash-cross-border, selective
  disclosure, or carrier requirements.

### 7.11 Open Interoperability API (Aligned with EN 18222)

DPP-CQ v2.0 defines a single open machine-to-machine API surface covering
passport creation, read, versioning/archiving, status/revocation and
cross-identifier searchability, expressed as a RESTful API (OpenAPI 3.0),
with normative provisions in
[api-specification.md](../interoperability/api-specification.md). It is
aligned with **EN 18222:2026 *Digital product passport — APIs for product
passport lifecycle management and searchability***:

- **Searchability:** a passport is locable by DID, GTIN, batch number, or a
  bound OID, with no prior bilateral arrangement between systems.
- **Gateway resolution:** read requests route to the authoritative data
  holder for the product, including across hybrid and cross-border
  deployments.
- **Open read, authorized depth:** public data (product identity, quality
  grade summary, issuer, privacy notice) is readable without registration or
  fee; business-sensitive and personal claims are released via credential
  exchange with selective disclosure.
- **Full lifecycle and persistence:** every state change produces a new hash
  anchor; revocation propagates across QR/NFC paths within SLA (target
  < 5 minutes); API requirements keep a passport retrievable even if the
  original economic operator ceases activity.
- The six Root Resolver endpoints in Annex A.3 are the discovery, status and
  anchoring subset of this surface. That subset alone is **DPP-CQ Read**
  conformance; issuer/node systems must implement the lifecycle and search
  methods to claim **DPP-CQ Lifecycle/Search** conformance.

---

## 8. Compliance & Legal Framework · 合规与法律框架

### 8.1 Data Sovereignty and Cross-Border Compliance Architecture

ICO standards employ an architectural design of **"data localization, hash cross-border"**, fundamentally reducing cross-border data compliance risks:

- **Raw data stored locally**: Detailed product quality, craftsmanship, and supply chain data are stored locally by the issuer or certification body, with no mandatory cross-border transmission
- **Hash fingerprint anchoring**: Only hash fingerprints of data (one-way irreversible) are registered and anchored at root nodes; hashes themselves contain no identifiable original information
- **Selective-disclosure verification**: Sensitive data is verified via SD-JWT / BBS+ selective disclosure; verifiers receive only the claims or compliance conclusions they are authorized for, without access to undisclosed raw data

This architecture is compatible with China's *Data Security Law* and *Personal Information Protection Law*, the EU's General Data Protection Regulation (GDPR), and the data sovereignty principles of most countries.

### 8.2 Compliance Adaptation by Major Jurisdictions

| Jurisdiction | Core Compliance Requirements | ICO Standard Adaptation |
|---|---|---|
| **China** | Data classification and grading, security assessment for outbound transfer of important data, critical information infrastructure protection; commercial cryptography requirements | Localized data storage, hash cross-border, independent deployment of domestic root nodes; optional SM2/SM3/SM4 cryptography suite; AI assessment transparency & human-oversight provisions (aligned with EU AI Act Art. 50 and ISO/IEC 42001); data lifecycle governance metadata |
| **European Union** | GDPR data protection; ESPR digital product passport & sustainability data; EN 18219/18220 series; EU AI Act transparency | SD-JWT/BBS+ selective disclosure, data minimization; GS1 Digital Link & EN 18220-aligned open carriers; ISO 14067 sustainability module; conformity claims; AI-use disclosure |
| **Southeast Asia** | Significant variation in national data protection laws, differing localization requirements | Flexible regional node deployment, configurable data storage strategies; lightweight L1 QR carrier for cost sensitivity |
| **Middle East / GCC** | Developing data localization and halal/cultural-product traceability regimes; strong interest in digital trade infrastructure | Regional node deployment; cultural-quality framing compatible with heritage-product protection; GS1/UNTP interop for trade |
| **Global South** | Relatively weak data regulations, insufficient digital capacity | Lightweight solutions, capacity building support, technology transfer; zero-licensing-fee adoption (see three red lines: no charging for standards use) |

### 8.2b International Interoperability Position

DPP-CQ is an **independent international standard** and does not subordinate
itself to any regional regulatory regime. Its interoperability strategy is
"baseline compatibility, differentiated value":

- **Baseline compatibility (non-negotiable interop):** open data carriers,
  global identifiers (GTIN alongside DID), standard credential formats
  (W3C VC / SD-JWT VC), standard APIs, and machine-readable conformity claims.
  These ensure DPP-CQ credentials can be read and cross-checked by EU DPP,
  retail, customs and GS1-based systems.
- **Differentiated value (kept independent):** the quality-and-culture
  assessment methodology (Std 3001), the multi-stakeholder governance model,
  affordability for small producers, and applicability to cultural product
  categories that environmental DPPs do not cover.
- **Multilateral bridge:** active engagement with the UN/CEFACT UNTP (UN Transparency
  Protocol) conformity-credential vocabulary and the ISO DPP
  work item (ISO/PWI 25534-1 track), so that DPP-CQ interops through neutral,
  multilateral standards rather than through any single jurisdiction's
  registry.

DPP-CQ's flagship categories (tea, wine & spirits, cultural crafts,
traditional medicine and health products, specialty agri-foods) are not within
the first ESPR priority product groups; the standard therefore has a strategic
window to mature its interop profile before any statutory DPP obligations
potentially reach its categories.

### 8.3 Data Lifecycle Governance

Every DPP-CQ credential in v2.0 carries a `dataLifecycle` record identifying
the data controller, retention policy, storage jurisdiction, cross-border mode
(default: hash-only), deletion/anonymization rules, privacy notice URI, and
PIA/DPIA summary URI. A public PIA summary is maintained at
[docs/compliance/pia-summary.md](../compliance/pia-summary.md), and
conformity declarations against the ESPR/EN framework, EU AI Act,
ISO/IEC 42001 and data-protection regimes are maintained at
[docs/compliance/conformity-declarations.md](../compliance/conformity-declarations.md).
Regulatory mappings for specific jurisdictions (including deployments within
China) are informative deployment-support material and do not constitute
normative references of the standard.

### 8.4 Electronic Evidence and Legal Effect

ICO standards are themselves technical and industry standards, without legal force (consistent with the nature of international standards such as those from ISO). However, their design fully considers judicial evidence requirements:

- **Hash integrity proof**: Cryptography-based data integrity verification can serve as electronic evidence in most jurisdictions
- **Trusted timestamps**: Integration with authoritative timestamp services meets the temporal certainty requirements for electronic evidence
- **Complete evidence chain**: Issuance chains, change records, and revocation logs constitute a complete evidence chain
- **Third-party audits**: Root nodes and core services undergo regular independent third-party audits to enhance evidentiary credibility

Specific legal effect varies by jurisdiction. ICO encourages regional nodes to collaborate with local legal institutions to promote recognition of the evidentiary weight of DPP-CQ credentials in their respective jurisdictions.

### 8.5 Dispute Resolution Mechanism

Referencing UNCITRAL (United Nations Commission on International Trade Law) arbitration rules and international commercial arbitration practices, ICO establishes a three-tier dispute resolution mechanism:

1. **Self-Help Mediation**: Parties negotiate independently through platform tools
2. **Expert Review**: A review panel composed of industry and technical experts issues a ruling
3. **Arbitration (Final)**: Submission to international commercial arbitration, with arbitral awards enforceable globally under the New York Convention

---

## 9. Getting Involved · 参与方式

### 9.1 Membership Categories

| Membership Category | Core Rights | Primary Obligations | Eligible Applicants |
|---|---|---|---|
| **Founding Member** | Council seats, priority participation, standard proposal rights | Annual contribution commitment, governance participation | Core founding institutions |
| **Contributing Member** | Working group participation, standard proposal rights, voting rights | Abide by charter, contribute to standard content | Enterprises, NGOs, academic institutions |
| **Adopting Member** | Free standard use, technical support, listing in ecosystem directory | Logo usage compliance, feedback on usage | Product manufacturers, service providers |
| **Community Member** | Participate in open-source community, submit feedback, attend public meetings | No mandatory obligations | Developers, researchers, individuals |

### 9.2 Participation Pathways

**Technical Participation:** Join the GitHub open-source community and contribute code, documentation, and technical solutions

**Standards Participation:** Apply to join relevant standards Working Groups (WGs) to participate in standard development and review

**Ecosystem Participation:** Become a verified service provider, regional node operator, or joint laboratory partner

**Adoption Participation:** Implement ICO standards in products or services and apply for DPP-CQ conformance assessment

---

## 10. Roadmap & Pilots · 路线图与试点规划

### 10.1 Three-Year Development Roadmap

**2026: Foundation and Ecosystem Launch Year**
- Q3: Publish governance standards and DPP-CQ v1.0
- Q3: Establish Technical Secretariat, launch Root Resolver Network
- Q4: Host Global Digital Credibility Governance Summit
- Q4: Publish GDCC standard draft
- Year-end target: 3+ standards published, 50+ member institutions, 1,000+ pilot products

**2027: Ecosystem Expansion and Regional Deployment Year**
- Publish 2–3 new standards (GI mutual recognition, haute couture, etc.)
- Launch 3 regional nodes: Southeast Asia, Middle East, Africa
- Establish 5+ industry joint laboratories
- 500+ institutional adopters, 10,000+ verified products
- Establish formal cooperation with 2–3 international standards organizations

**2028 and Beyond: Global Mutual Recognition and Ecosystem Maturity Year**
- 10+ standards published
- 20+ national/regional nodes
- 1,000+ institutional adopters, 100,000+ verified products
- Establish mutual recognition mechanisms with major international standards organizations

### 10.2 Initial Pilot Framework

The first batch of flagship product assessment pilots will launch in the second half of 2026:

| Pilot Category | Flagship Direction | Collaboration Model | Success Metrics |
|---|---|---|---|
| GI Tea | Top-tier production region GI tea | Production region + brand joint assessment | Number of verified SKUs, traceability data coverage rate |
| ICH Ceramics | Handcrafted technique heritage | Artisan + production region joint | Cultural data completeness, user verification volume |
| Haute Couture Attire | Chinese haute couture brands | Brand assessment + craft evidence anchoring | Full lifecycle passport coverage, market feedback |
| ICH Handicrafts | Embroidery / lacquerware, etc. | Transmitters + institutional joint | ICH value display, cross-border transaction improvement |

Pilot evaluation dimensions: number of verified products, traceability data quality, user verification frequency, cross-border transaction improvement, producer value gain.

---

## 11. Risks & Challenges · 风险与挑战

| Risk | Description | Mitigation Strategy |
|---|---|---|
| **Adoption Resistance** | SMEs have limited digital capabilities and concerns about integration costs | Provide lightweight toolkits, SaaS platforms, capacity building programs; free during the first 6-month pilot period |
| **Privacy and Data Security** | High protection requirements for cultural craftsmanship and commercial data | Strict selective-disclosure application, off-chain storage architecture, regular third-party security audits; data control rests with issuers |
| **Standards Fragmentation** | Multiple sets of DPP standards coexist globally, creating confusion for enterprises | Actively promote mutual recognition and compatibility; participate in multilateral interoperability initiatives such as UNECE; avoid closed systems |
| **Governance Neutrality** | International community has concerns about the fairness of standard-setting | Transparent governance processes, multi-party oversight mechanisms, independent third-party audits, balanced representation |
| **Technology Evolution Risk** | Cryptography and blockchain technologies evolve rapidly, risking standard obsolescence | Modular design, extensible architecture, periodic technical reviews, backward compatibility strategy |
| **Geopolitical Risk** | Changes in international landscape may affect global acceptance of the standard | Maintain technology-neutral positioning, de-emphasize geopolitical coloring, focus on solving real problems as the core driving force |

---

## 12. Conclusion · 结语

In the digital age, trust is the most precious public good.

From the Industrial Revolution to the Information Revolution, every leap in human society has been accompanied by iterations in trust mechanisms. Today, as digital technology reshapes global trade and cultural exchange at an unprecedented pace, we need a more inclusive and pluralistic digital trust infrastructure — one that not only serves efficiency optimization for industrial products but also safeguards the diversity of human culture, ensuring that the unique value of every civilization can be seen, recognized, and respected in the digital world.

The ICO standards framework is committed to providing open, neutral, and inclusive digital trust infrastructure for global cultural and quality assets. We are not building a closed standards system; rather, we are contributing to the global digital trust edifice — using W3C's technical language to write chapters of cultural value; using multi-stakeholder governance wisdom to build cross-cultural bridges of trust.

We look forward to a future where every product carrying human wisdom and cultural value possesses a trustworthy digital identity — making global trade fairer, cultural heritage more vibrant, and the digital economy more human-centered.

**We invite stakeholders worldwide to submit revision proposals by August 20, 2026 (Accelerated Procedure · 45-day review period), and to join us in building a more inclusive global digital trust future.**

---

## Annex A (Normative): DPP-CQ Technical Specification Draft
### 附录A（规范性）DPP-CQ技术规格草案

> This annex presents a summary of the DPP-CQ standard technical specification draft. The complete technical specification will be published in the official version of ICO Std 2001-2026.

### A.1 DID Identifier Format

The DPP-CQ product DID uses the `did:ico:dpp` method name, with the following format:

```
did:ico:dpp:<namespace>:<unique-id>
```

- `namespace`: Category or issuer namespace (e.g., `tea`, `ceramic`, `fashion`)
- `unique-id`: Product unique identifier; UUID v4 or GS1-like coding is recommended

Examples:
```
did:ico:dpp:tea:longjing-xh-2026-001
did:ico:dpp:ceramic:jz-yd-2026-0892
```

A product that also holds a formally allocated ISO/ITU-T Object Identifier
binds it at the application layer: the DID document carries the OID in
`alsoKnownAs` as an `urn:oid:` URN (RFC 3061), and the credential repeats the
equivalence in `identifiers.alias`. The DID remains the canonical identifier;
the binding rules (bidirectional agreement, registered OID only) are defined
normatively in [identifier-mapping.md](../interoperability/identifier-mapping.md).

### A.2 JSON-LD Context Example

The JSON-LD context definition for DPP-CQ credentials:

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://www.w3.org/2018/credentials/examples/v1",
    "https://icoun.org/contexts/dpp-cq/v1"
  ],
  "id": "did:ico:dpp:tea:longjing-xh-2026-001",
  "type": ["VerifiableCredential", "DPPQualityCredential", "CulturalHeritageCredential"],
  "issuer": "did:ico:issuer:zjtea-assoc",
  "issuanceDate": "2026-07-15T00:00:00Z",
  "expirationDate": "2027-07-14T23:59:59Z",
  "credentialSubject": {
    "id": "did:ico:dpp:tea:longjing-xh-2026-001",
    "productName": "西湖龙井茶",
    "category": "geographical-indication-tea",
    "qualityGrade": "Premium",
    "origin": {
      "type": "GeographicalIndication",
      "giNumber": "GI-CN-0001",
      "region": "杭州西湖产区",
      "country": "CN"
    },
    "culturalData": {
      "heritageStatus": "National Intangible Cultural Heritage",
      "heritageYear": 2008,
      "craftMethod": "手工炒制 · 十大手法",
      "artisanInfo": {
        "name": "（可选，经授权披露）",
        "generation": "第5代传承人"
      }
    },
    "traceability": {
      "harvestDate": "2026-03-28",
      "processLocation": "杭州龙坞茶镇",
      "batchNumber": "XH20260328A01"
    },
    "qualityAttributes": {
      "appearance": "扁平光滑，色泽嫩绿",
      "aroma": "嫩香持久",
      "taste": "鲜醇甘爽"
    }
  },
  "proof": {
    "type": "BbsBlsSignature2020",
    "created": "2026-07-15T10:30:00Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:ico:issuer:zjtea-assoc#keys-1",
    "proofValue": "..."
  }
}
```

### A.3 Root Resolver Node API (Discovery / Status / Anchoring Subset)

The six endpoints below are the discovery, status and hash-anchoring subset
exposed by a Root Resolver node. The complete open interoperability API for
passport lifecycle management and searchability (resource model, identifier
search by GTIN/OID/batch, lifecycle methods, conformance levels) is defined
normatively in [api-specification.md](../interoperability/api-specification.md),
aligned with EN 18222:2026.

| Endpoint | Method | Function |
|---|---|---|
| `/v1/did/{did}` | GET | Query DID document |
| `/v1/credential/{credentialId}/status` | GET | Query credential status (valid/revoked/expired) |
| `/v1/credential/verify` | POST | Verify credential signature and validity |
| `/v1/register` | POST | Register new credential hash |
| `/v1/revoke` | POST | Revoke credential |
| `/v1/proof/{hash}` | GET | Obtain hash anchoring proof |

### A.4 Three-Tier Verification Process

```
Scan QR / NFC Tap
    │
    ├── Quick Verification (<1s)
    │   └── Verifies: DID validity + Credential status + Basic information
    │
    ├── Deep Verification (3–5s)
    │   └── Verifies: Complete credential signature chain + Traceability data
    │                    + Quality details + ZKP proof
    │
    └── Judicial-Grade Verification (application required)
        └── Verifies: Root node anchored hash + Timestamp proof
                     + Complete audit trail
```

---

## Annex B (Informative): Glossary
### 附录B（资料性）术语表

| Term | Definition |
|---|---|
| **Digital Product Passport (DPP)** | A digital identity credential containing core product data, readable via methods such as code scanning |
| **Decentralized Identifier (DID)** | A decentralized identity identifier defined by W3C, independent of centralized identity providers |
| **Verifiable Credential (VC)** | A digital credential digitally signed by the issuer, independently verifiable by third parties |
| **Selective Disclosure (SD-JWT / BBS+)** | Cryptographic proofs (SD-JWT per RFC 9529; BBS+ unlinkable derived credentials) that let a holder reveal only selected claims while keeping the signature valid; v1.x used the umbrella term "zero-knowledge proofs (ZKP)", v2.0 normatively uses these standard suites |
| **Selective Disclosure** | The practice by which a data holder discloses only the necessary data fields to a verifier |
| **Geographical Indication (GI)** | An indication identifying a product as originating from a specific territory, where a given quality, reputation, or other characteristic of the product is essentially attributable to its geographical origin |
| **Intangible Cultural Heritage (ICH)** | Practices and expressions recognized by communities, groups, and, in some cases, individuals as part of their cultural heritage, as defined by UNESCO |
| **Root Resolver** | A unified resolution and anchoring infrastructure for globally distributed identifiers |
| **Object Identifier (OID)** | An internationally unique hierarchical identifier allocated under the registration tree defined by ITU-T X.660 / ISO/IEC 9834-1, used in certificates, registries and enterprise systems; expressed in dotted notation, as OID-IRI, or as an `urn:oid:` URN (RFC 3061) |
| **Hash Anchoring** | Storing hash fingerprints of data on tamper-proof media for integrity verification and timestamping |
| **JSON-LD** | JSON for Linked Data — a JSON format for linked data, supporting semantic interoperability |
| **Multi-Stakeholder Governance** | A governance model ensuring that all parties affected by decisions have the opportunity to participate in decision-making |

---

## Annex C (Informative): Abbreviations
### 附录C（资料性）缩略语

| Abbreviation | Full Form |
|---|---|
| ICO | International Communication Organization 国际传播组织 |
| DPP | Digital Product Passport 数字产品护照 |
| DPP-CQ | Digital Product Passport for Cultural & Quality Goods 文化与品质数字产品护照 |
| DID | Decentralized Identifier 分布式标识符 |
| VC | Verifiable Credential 可验证凭证 |
| ZKP | Zero-Knowledge Proof 零知识证明 |
| GI | Geographical Indication 地理标志 |
| ICH | Intangible Cultural Heritage 非物质文化遗产 |
| GDCC | Global Digital Credibility Assessment 全球数字公信力评定 |
| TCR | Tianji Credibility Registry 天机可信价值评级数据库 |
| GDC | Global Digital Compact 全球数字契约 |
| W3C | World Wide Web Consortium 万维网联盟 |
| WIPO | World Intellectual Property Organization 世界知识产权组织 |
| UNESCO | United Nations Educational, Scientific and Cultural Organization 联合国教科文组织 |
| ISO | International Organization for Standardization 国际标准化组织 |
| IETF | Internet Engineering Task Force 互联网工程任务组 |
| UNECE | United Nations Economic Commission for Europe 联合国欧洲经济委员会 |
| ESPR | Ecodesign for Sustainable Products Regulation 可持续产品生态设计法规 |
| GS1 | Global Standard 1 国际物品编码组织 |
| GDPR | General Data Protection Regulation 通用数据保护条例 |
| UNCITRAL | United Nations Commission on International Trade Law 联合国国际贸易法委员会 |
| NFC | Near Field Communication 近场通信 |
| OID | Object Identifier 对象标识符 |
| OID-IRI | Object Identifier Internationalized Resource Identifier 对象标识符国际化资源标识符 |
| API | Application Programming Interface 应用程序接口 |
| REST | Representational State Transfer 表述性状态传递 |
| CLA | Contributor License Agreement 贡献者许可协议 |

---

## Annex D (Informative): References
### 附录D（资料性）参考文献

1. United Nations. *A Global Digital Compact — Our Shared Agenda*. 2024.
2. WIPO (2024). *World Intellectual Property Indicators 2024*. Geneva: World Intellectual Property Organization.
3. UNESCO. *Convention for the Safeguarding of the Intangible Cultural Heritage*. 2003.
4. UNESCO. *Operational Directives for the Implementation of the Convention for the Safeguarding of the Intangible Cultural Heritage*. 2016/2018.
5. OECD/EUIPO. *Mapping Global Trade in Fakes 2025: Global Trends and Enforcement Challenges*. Paris: OECD Publishing, 2025.
6. W3C. *Decentralized Identifiers (DIDs) v1.0*. W3C Recommendation, July 2022.
7. W3C. *Verifiable Credentials Data Model v2.0*. W3C Recommendation, May 2025.
8. UNECE. *Global Digital Product Passport Interoperability Initiative*. United Nations Economic Commission for Europe.
9. European Commission. *Proposal for a Regulation on Ecodesign for Sustainable Products (ESPR)*. 2022.
10. OECD. *Enhancing Digital Trust for All*. 2024.
11. World Bank. *Digital Economy and Inclusive Growth*. 2023.
12. UNCITRAL. *UNCITRAL Model Law on Electronic Commerce*.
13. ISO. *ISO 22000: Food Safety Management Systems*. International Organization for Standardization.
14. GS1. *EPCIS 2.0 and Core Business Vocabulary (CBV)*. GS1 Standard.
15. IETF. *RFC 9529 — SD-JWT: Selective Disclosure for JWTs (SD-JWT)*. 2024.
16. W3C. *Verifiable Credential Data Integrity 1.0* (EdDSA / BBS cryptosuites). W3C Recommendations.
17. GS1. *GS1 Digital Link: URI Syntax*, version 1.6. GS1 Standard, 2024.
18. CEN-CENELEC JTC 24. *EN 18216:2026 / EN 18219–18223:2026* — Digital Product Passport horizontal standards. 2026.
19. European Union. *Regulation (EU) 2024/1689 (AI Act)*, Art. 50; *Regulation (EU) 2023/1542 (Batteries)*.
20. ISO. *ISO 14067:2018 — Greenhouse gases — Carbon footprint of products*.
21. UN/CEFACT. *UN Transparency Protocol (UNTP) — Conformity Credential specification*. untp.unece.org.
22. ISO/IEC. *ISO/IEC 42001:2023 — Artificial intelligence — Management system*.
23. IETF. *The BBS Signature Scheme*. IETF Draft.
24. CEN-CENELEC JTC 24. *EN 18222:2026 — Digital product passport — Application Programming Interfaces (APIs) for the product passport lifecycle management and searchability*. 2026.
25. ITU-T / ISO/IEC. *X.660 | ISO/IEC 9834-1:2012 — Information technology — Procedures for the operation of object identifier registration authorities*.
26. ITU-T / ISO/IEC. *X.680 | ISO/IEC 8824-1 — Abstract Syntax Notation One (ASN.1): Specification of basic notation*.
27. IETF. *RFC 3061 — A URN Namespace of Object Identifiers*.
28. ISO/IEC. *ISO/IEC 14443 (Identification cards — Contactless integrated circuit cards — Proximity cards), ISO/IEC 18004 (QR code symbology), ISO/IEC 15415 (bar code symbol print quality)*.

---

## Annex E (Informative): Frequently Asked Questions
### 附录E（资料性）常见问题

### Q1: What is ICO? What qualifications does it have to develop international standards?

ICO (International Communication Organization) is a multi-stakeholder international cooperation platform dedicated to advancing global digital inclusion and cross-cultural digital trust.

The ICO standards framework employs an open community-driven development model, following best practices in international standard-setting (openness, transparency, consensus, balanced representation). The vitality of standards lies in adoption and ecosystem, not administrative mandate — the core Internet protocols (TCP/IP, HTTP, etc.) were not promulgated by governments or official bodies, but became de facto standards through joint advancement by open-source communities and standards organizations and widespread market adoption. ICO is committed to becoming the de facto standard-setter in the field of cultural and quality digital trust.

### Q2: What is the relationship between ICO standards and the EU DPP? Will they conflict?

A complementary relationship, not a competitive one.

The EU DPP (under the ESPR framework) focuses primarily on environmental and circular economy data for industrial products — a "green dimension" Digital Product Passport. ICO DPP-CQ focuses on the cultural value and quality dimensions of cultural products and specialty agricultural goods — a "cultural dimension" Digital Product Passport. The two cover different product categories and data dimensions; they are complementary rather than substitutive.

At the technical level, DPP-CQ is fully compatible with W3C DID/VC standards, sharing the same technical foundation as the EU DPP, enabling data interoperability. v2.0 makes this concrete: products in the GS1 interop profile carry GTIN identifiers and open GS1 Digital Link carriers (aligned with EN 18219/18220), credentials support SD-JWT VC (RFC 9529) alongside BBS+, and sustainability data follows ISO 14067 and UNTP-style conformity claims, so EU importers and regulators can read and cross-check DPP-CQ data with standard tooling. DPP-CQ's flagship categories (tea, wine & spirits, cultural crafts, traditional medicine products) are not in the first ESPR priority product groups, so there is no statutory conflict; the two regimes address different dimensions and can be carried by the same passport. We welcome standard coordination and mutual recognition dialogue with relevant EU institutions.

### Q3: Why is a Root Resolver Network needed? Will it create a monopoly?

The core function of the Root Resolver Network is to ensure consistency of DID resolution and queryability of credential status in global cross-border circulation. This is analogous to the root servers of the Domain Name System (DNS) — not for the purpose of monopolization, but for the purpose of interoperability.

The design of the root resolution mechanism follows the following principles:
- **Technology-neutral**: Root nodes only provide resolution and anchoring services; they do not participate in standard-setting and do not engage in commercial competition;
- **Governance constraints**: Root node operation is overseen by the Technical Committee and authorized by the Standards Council; major changes require approval through governance processes;
- **Gradual decentralization**: The long-term goal is to establish a distributed root node network with multiple regions and multiple operators, avoiding single-point dependencies;
- **Open source and open**: The reference implementation of root nodes is fully open-source, and any institution may deploy a compatible node.

### Q4: How are data security and privacy ensured? Will data exit issues arise?

ICO standards employ an architectural design of "data localization, hash cross-border":
- **Raw data stored locally**: Detailed product quality, craftsmanship, and supply chain data are stored locally by the issuer or certification body, with no mandatory cross-border transmission;
- **Hash fingerprint anchoring**: Only hash fingerprints of data (one-way irreversible) are registered and anchored at root nodes; hashes themselves contain no identifiable original information;
- **Selective disclosure**: Sensitive data is verified via SD-JWT / BBS+ proofs; verifiers receive only the claims or compliance conclusions they are authorized for, without access to undisclosed raw data;
- **Compliance adaptation**: Regional nodes may conduct localized deployment and compliance adjustments in accordance with local data regulations.

This architecture fundamentally reduces the risk of cross-border flow of raw data and complies with regulatory requirements for data sovereignty and data security in all countries.

### Q5: What is the relationship between the Tianji system and ICO?

The Tianji system (天机体系) is one of the institutions undertaking the role of Technical Secretariat for the ICO standards framework, responsible for reference implementation of standards, root node operation and maintenance, and technical support.

This arrangement is analogous to the relationship between W3C and host institutions such as MIT/ERCIM — standards are developed jointly by the community, and the Technical Secretariat is responsible for execution and implementation. The Tianji system, as a technical service provider, does not participate in standard voting, ensuring separation of standard-setting from technical execution.

### Q6: Is there a fee to adopt ICO standards?

The standards themselves are completely free.
- Standards documentation: Free to download and use (CC BY 4.0 / Apache 2.0)
- Reference implementations: Open-source and free, freely modifiable and commercially usable
- Basic verification: Basic functions such as scan-to-verify are freely available

Value-added services (such as custom development, advanced assessment services, technical support, etc.) may be provided by service providers in the ecosystem; ICO itself does not directly operate commercial services.

### Q7: What is the relationship with GS1 and ISO? Is this a separate stovepipe effort?

No, it is not a separate stovepipe effort. ICO standards are built upon existing international standards such as W3C, ISO, and GS1, serving as a supplement and extension of the existing standards ecosystem in the cultural and quality dimensions.

W3C DID is the "technical standard for ID cards" (telling us how to make the card), ISO/GS1 is the "industry coding specification" (telling us how to number things), and ICO DPP-CQ is the "content specification for cultural product passports" (telling us what content goes in the passport and how to verify cultural value). We use W3C's card technology, are compatible with GS1's coding system, and focus on content standards for the vertical domain of culture and quality.

We actively seek cooperation and mutual recognition with standards organizations such as ISO, W3C, and GS1.

### Q8: Can small and medium-sized producers afford it? Will it increase their burden?

This is precisely one of the core concerns of ICO standards.

Our design goal is to enable small and medium-sized producers and ICH transmitters to "afford and benefit from" the system:
- **Low-cost solutions**: Support low-cost verification methods such as QR codes, with startup costs as low as a few cents per item;
- **Lightweight onboarding**: SaaS-based assessment platforms are provided, requiring no technical team — usable upon registration;
- **Volume discounts**: Discounts or waivers for small and medium-sized producers and ICH transmitters;
- **Capacity building**: Training and technical support provided through regional nodes and partners.

We believe that the "premium for quality" effect brought by digital passports will far exceed their usage cost — helping good products command good prices is the most direct value empowerment for producers.

### Q9: What about the legality and evidentiary effect of the standards?

ICO standards are themselves a set of technical and industry standards, without legal force (consistent with the nature of international standards such as those from ISO). However, their design fully considers judicial evidence requirements:

- **Hash anchoring**: Cryptography-based data integrity proof can serve as electronic evidence in most jurisdictions;
- **Trusted timestamps**: Integration with authoritative timestamp services meets the temporal certainty requirements for electronic evidence;
- **Complete evidence chain**: Issuance chains, change records, and revocation logs constitute a complete evidence chain;
- **Third-party audits**: Root nodes and core services undergo regular independent third-party audits to enhance evidentiary credibility.

Specific legal effect varies by jurisdiction. ICO encourages regional nodes to collaborate with local legal institutions to promote recognition of the evidentiary weight of DPP-CQ credentials in their respective jurisdictions.

### Q10: How is the neutrality of the standards ensured? How can we be certain no single party dominates?

The multi-stakeholder governance mechanism is the institutional guarantee for standard neutrality:

- **Balanced representation**: Council seats are allocated by category (government 25%, industry 25%, academia 20%, civil society 20%, Technical Secretariat 10% non-voting), so no single group can dominate decision-making;
- **Consensus-first**: Important decisions prioritize seeking consensus rather than simple majority voting;
- **Separation of technology and standards**: The Technical Secretariat does not participate in standard voting, separating execution from decision-making;
- **Transparency and openness**: Governance processes are open and transparent, subject to community oversight;
- **Open participation**: Any institution may apply to join, regardless of nationality, size, or ownership structure.

---

## How to Cite This Document · 如何引用本文档

**English Citation:**
> International Communication Organization (ICO). *DPP-CQ: Digital Product Passport for Cultural & Quality Goods — Standard Architecture and Core Specifications*[R]. ICO-TS-001:2026, v2.0.0-draft (Public Review Draft). August 2026. https://github.com/ICO-cloud/dpp-cq-standard

**中文引用格式：**
> 国际传播组织（ICO）. DPP-CQ文化与品质数字产品护照：标准架构与核心规范[R]. ICO-TS-001:2026, v2.0.0-draft（征求意见稿）. 2026年8月. https://github.com/ICO-cloud/dpp-cq-standard

---

## Annex F (Normative): v2.0 Interoperability & Compliance Annexes
### 附录F（规范性）v2.0 互操作与合规附件

The following separate documents form a normative part of ICO Std 2001 v2.0. They are maintained in the repository under `docs/`:

| Document | Path | Content |
|---|---|---|
| **GS1 Digital Link & Identifier Mapping** | `docs/interoperability/gs1-digital-link-mapping.md` | GTIN↔DID binding rules, Digital Link URI structure and content negotiation, EPCIS 2.0 event mapping, EN 18219/18220 alignment |
| **Data Carrier Specification** | `docs/interoperability/carrier-specification.md` | Three-tier carriers (L1 open QR / L2 SDM NFC / L3 tamper-evident NFC), open-carrier principle, dual-carrier rule, resolver behavior; ISO/IEC 14443 Type 4, ISO/IEC 18004, ISO/IEC 15415 baselines |
| **Identifier Mapping: OID ↔ DID** | `docs/interoperability/identifier-mapping.md` | Application-layer equivalence binding via DID `alsoKnownAs` and credential `identifiers.alias`; X.660/9834-1 and 8824-1; no new DID method, no root-resolver change |
| **Open Interoperability API** | `docs/interoperability/api-specification.md` | REST API aligned with EN 18222:2026: resource model, lifecycle methods, identifier searchability, Read/Lifecycle/Search conformance levels, error and non-functional requirements |
| **Credential Format Profiles** | `docs/specs/credential-formats.md` | JSON-LD Data Integrity (BBS+) vs SD-JWT VC (RFC 9529) profiles; disclosure classification; SM2/SM3/SM4 optional regional cryptography suite; status and validity rules |
| **Conformity Declarations** | `docs/compliance/conformity-declarations.md` | Self-declarations against EU ESPR/EN standards, ISO/IEC 42001, GDPR/PIPL, EU AI Act; jurisdiction-specific mappings are informative |
| **PIA / DPIA Summary** | `docs/compliance/pia-summary.md` | Public privacy impact assessment: data flows, risk table, data-subject rights, cross-border legal basis |
| **JSON Schema v2.0** | `schemas/dpp-cq.schema.json` | Machine-readable data model ($id: icoun.org/schemas/dpp-cq/v2.0.0-draft) |
| **v2.0 Example Credential** | `examples/longjing-tea-v2.json` | Full interop-profile example (Longjing tea) |

### Relationship to external frameworks

| External framework | Nature | DPP-CQ posture |
|---|---|---|
| W3C DID / VC v2.0, IETF SD-JWT (RFC 9529) | Open standards | Foundation; fully adopted |
| GS1 Digital Link / EPCIS 2.0 | Global supply-chain standards | Normative interop profile |
| EU ESPR (Reg. 2024/1781); EN 18216–18223 (incl. EN 18222 APIs) | EU regulation / harmonized standards | Baseline compatibility for carriers, identifiers, APIs, sustainability fields; DPP-CQ categories not in first priority groups |
| UN/CEFACT UNTP | UN multilateral vocabulary | Adopted for conformity claims; primary multilateral bridge |
| ISO/IEC 14067, 22000, 22739, 42001, 14443, 18004, 15415 | ISO standards | Referenced in data model, terminology, AI governance and carrier baselines |
| ITU-T X.660 / ISO/IEC 9834-1; X.680 / ISO/IEC 8824-1; RFC 3061 (OID) | International identifier standards | Application-layer OID ↔ DID binding; no new DID method |
| SM2/SM3/SM4 (GB/T 32918/32905/32907) | Regional cryptography standards | Opt-in suite for deployments within jurisdictions that require it |
| EU AI Act (Reg. 2024/1689) Art. 50; ISO/IEC 42001 | EU regulation / ISO standard | Transparency and AI management provisions adopted as baseline practice |

---

**Published by · 发布机构**: International Communication Organization (ICO) 国际传播组织
**Document No. · 文档编号**: ICO-TS-001:2026
**Version · 版本**: v2.0.0-draft
**Status · 状态**: Public Review Draft · 征求意见稿（第二轮）
**Issued · 发布日期**: August 2026 · 2026年8月
**Comment Deadline · 意见征集截止**: October 15, 2026 (second review round: international interoperability & compliance) · 2026年10月15日（第二轮：国际互操作与合规）
**Feedback · 反馈**: info@icoun.org
**Repository · 仓库**: https://github.com/ICO-cloud/dpp-cq-standard

---

*This is a public review draft. Content is subject to change based on community feedback. The official version published by ICO shall prevail.*

*本文档为征求意见稿，内容可能根据社区反馈进行修改。正式版本以ICO官方发布为准。*

*© 2026 International Communication Organization (ICO). This work is licensed under a Creative Commons Attribution 4.0 International License.*
