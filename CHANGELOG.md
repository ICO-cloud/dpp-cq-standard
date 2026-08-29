# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0-draft] - 2026-08

### Added
- **GS1 interop profile (normative):** GTIN/GLN identifier binding with DIDs, GS1 Digital Link 1.6 URI structure with content negotiation, EPCIS 2.0/CBV 2.0 event mapping (`docs/interoperability/gs1-digital-link-mapping.md`)
- **Three-tier carrier specification (normative):** L1 open QR / L2 SDM secure NFC (NTAG 424 DNA class) / L3 tamper-evident NFC; open-carrier principle aligned with EN 18220:2026 and ESPR Art. 9; dual-carrier rule (`docs/interoperability/carrier-specification.md`)
- **Dual credential format profiles (normative):** W3C Data Integrity (BBS+ unlinkable selective disclosure) and IETF SD-JWT VC (RFC 9529, ecdsa-sd-2023); disclosure classification table (`docs/specs/credential-formats.md`)
- **Chinese national cryptography suite (optional):** SM2/SM3 (GB/T 32918/32905) signature suite `sm2-with-sm3-2026`, SM4 (GB/T 32907) for payload encryption, region-scoped opt-in
- **Sustainability data module:** ISO 14067-aligned product carbon footprint, materials/recycled content, end-of-life guidance — quality + sustainability dual-dimension data model
- **AI-assisted assessment transparency:** mandatory `aiDisclosure`, human final decision, methodology reference — aligned with GB/T 47507-2026 and EU AI Act Art. 50
- **Data lifecycle governance metadata:** controller, retention, storage jurisdiction, cross-border mode, deletion policy, privacy notice and PIA URIs
- **Conformity claims:** UNTP-style machine-readable conformity claim structure for cross-regime mapping (ESPR, EN standards, GB/T standards)
- **Compliance document set:** conformity declarations against GB/T 47507-2026, ESPR/EN, GDPR/PIPL, AI Act (`docs/compliance/conformity-declarations.md`); public PIA/DPIA summary (`docs/compliance/pia-summary.md`)
- **JSON Schema v2.0** (`schemas/dpp-cq.schema.json`) and full interop-profile example (`examples/longjing-tea-v2.json`)
- New product categories: wine-and-spirits, traditional-medicine-health, light-consumer-goods
- Second public review period: September 1 – October 15, 2026

### Changed
- Terminology alignment: system-internal "certification" wording replaced with assessment/evaluation/verification (评定/评价/验证) per market-regulation compliance; "ICO Certified" mark renamed "ICO Verified"
- Technical stack table expanded with SD-JWT, GS1 Digital Link, EPCIS, national cryptography, sustainability standards
- Interoperability strategy restated as "baseline compatibility, differentiated value" with UNTP as the multilateral bridge
- Jurisdiction compliance table expanded (China cryptography & AI standards, EU EN series & AI Act, GCC/Middle East)
- W3C VC v2.0 validity terms (`validFrom`/`validUntil`) accepted alongside legacy `issuanceDate`/`expirationDate`
- Status list guidance updated to BitstringStatusList

### Notes
- All v2.0 additions are OPTIONAL; v1.x credentials remain valid (minor-version backward compatibility per §7.6)

## [1.3.0] - 2026-07-06

### Added
- Scope and Purpose sections (W3C-style front matter)
- "How to Cite This Document" section with CN/EN citation formats
- DPP-CQ JSON Schema (draft 2020-12)
- Complete DPP-CQ example credential (Longjing tea use case)
- Code of Conduct (Contributor Covenant v2.1)

### Changed
- **Title updated**: Main title now leads with "DPP-CQ" for alignment with Global Digital Compact nomenclature
- "本白皮书" → "本文档" throughout, establishing technical specification positioning
- WIPO reference corrected to *World Intellectual Property Indicators 2024* (Geneva: WIPO)
- UNESCO ethical principles reference updated to *Operational Directives for the Implementation of the Convention for the Safeguarding of the Intangible Cultural Heritage* (2016/2018)
- Market size data updated from un-sourced WIPO "$50B" to OECD & EUIPO verified $467B (2021)
- Removed "world's first" and other absolute claims
- "绝对安全" → "高安全性" (high security posture)
- Format normalized to international technical specification standard: document header, abstract, status section, revision history, normative/informative appendix classification

### Fixed
- WIPO-WTO-WTO typo in references
- Inconsistent terminology across sections

## [1.2.0] - 2026-07-06

### Added
- Compliance & Legal Framework chapter
- DPP-CQ Technical Specification Appendix (Draft)
- Intellectual Property Policy
- Standard Version Management Strategy
- FAQ section (Appendix)
- Strengthened UNESCO/WIPO/UNECE references

## [1.1.0] - 2026-07-05

### Added
- Complete 12-chapter architecture
- Technical implementation details
- Governance framework
- Roadmap and pilot planning

## [1.0.0] - 2026-07-05

### Added
- Initial white paper release
- Core DPP-CQ concept and architecture
- ICO standards framework overview
