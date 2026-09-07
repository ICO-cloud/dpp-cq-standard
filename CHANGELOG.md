# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0-draft] - 2026-09-07

### Added
- **Normative Annex: GS1 Digital Link & Identifier Mapping** (`docs/interoperability/gs1-digital-link-mapping.md`): GTIN↔DID binding rules, Digital Link URI structure and content negotiation, EPCIS 2.0 event mapping, EN 18219/18220 alignment
- **Normative Annex: Data Carrier Specification** (`docs/interoperability/carrier-specification.md`): Three-tier carriers (L1/L2/L3), open-carrier principle, dual-carrier rule, resolver behavior
- **Normative Annex: Credential Format Profiles** (`docs/specs/credential-formats.md`): BBS+ (JSON-LD Data Integrity) vs SD-JWT VC profiles; disclosure classification (P/H/R); SM2/SM3/SM4 optional suite
- **Normative Annex: Conformity Declarations** (`docs/compliance/conformity-declarations.md`): Self-declarations against GB/T 47507-2026, EU ESPR/EN, GDPR/PIPL, EU AI Act
- **Normative Annex: PIA/DPIA Summary** (`docs/compliance/pia-summary.md`): Public privacy impact assessment with data flows, risk register, data subject rights, cross-border legal basis
- **v2.0 Example Credential** (`examples/longjing-tea-v2.json`): Full interop-profile example demonstrating GS1 Digital Link, dual-carrier (L2+L1), AI disclosure, sustainability module, data lifecycle governance

### Changed
- **JSON Schema upgraded to v2.0.0-draft** (`schemas/dpp-cq.schema.json`): `$id` updated; added sustainability, aiDisclosure, dataLifecycle, carrierTier, gs1DigitalLink modules; VC 2.0 terminology (validFrom/validUntil); issuer as object support; EPCIS event type mapping; UNTP conformity claim references

---

## [2.0.0-draft] - 2026-09-01

### Added
- **GS1 Digital Link interoperability**: Native GS1 Digital Link URI syntax for carrier identification
- **Three-tier carrier specification**: L1 (Open QR), L2 (SDM Secure NFC), L3 (Tamper-evident NFC)
- **SD-JWT VC credential format**: IETF RFC 9529 support alongside BBS+ selective disclosure
- **Chinese cryptography optional module**: SM2/SM3/SM4 support per GM/T 0009, GM/T 0004, GM/T 0002
- **Sustainability module**: ISO 14067 carbon footprint disclosure requirements
- **AI transparency disclosure**: EU AI Act Art.50 and GB/T 47507-2026 compliance
- **Governance Charter v0.5**: Open multi-stakeholder governance framework defining membership, voting, IPR policy, and dispute resolution
- **White Paper v2.0**: Comprehensive architecture overview with all v2.0 enhancements

### Changed
- **Standard numbering**: Unified to ICO Std 2001 (previously ICO-TS-001)
- **Public review period**: Second review Sep 1 – Oct 15, 2026 (previously Jul 6 – Aug 20, 2026)
- **Carrier specification**: Expanded from dual-tier to three-tier (L1/L2/L3)
- **Credential formats**: Now supports both BBS+ and SD-JWT VC
- **Documentation portal**: Launched dedicated standard portal at dppcq.org
- **Demo**: Published reference implementation at ico-cloud.github.io/dpp-cq-demo

### Fixed
- Various technical clarifications based on first public review feedback
- Terminology consistency across specification and white paper
- Cross-reference alignment between documents

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
- Inconsistent terminology across documents

## [1.0.0] - 2026-05-15

### Added
- Initial public release
- Core DPP-CQ data model
- Basic carrier specification (QR + NFC)
- BBS+ credential format
- White Paper v1.0 (CN + EN)
