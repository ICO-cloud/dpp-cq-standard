# Conformity Declarations
## Normative Annex — ICO Std 2001 v2.0

> **Status**: Normative · Part of ICO Std 2001:2026 (DPP-CQ v2.0)
> **Maintained at**: `docs/compliance/conformity-declarations.md`
> **Version**: 2.0.0-draft

---

## 1. Scope

This annex contains self-declarations of conformity made by ICO against
relevant regulatory frameworks and standards. These declarations are
maintained as part of the standard and are updated as frameworks evolve.

Aligned with UNTP-style conformity claims (white paper §8.2b).

## 2. Declaration Framework

Each declaration follows this structure:

| Field | Description |
|---|---|
| **Framework** | The external regulation or standard |
| **Scope** | What aspects of DPP-CQ are covered |
| **Conformity level** | Full / Partial / Aligned |
| **Evidence** | How conformity is demonstrated |
| **Limitations** | Known gaps or areas of non-conformity |

## 3. AI Trustworthiness: GB/T 47507-2026

**Framework**: GB/T 47507-2026 — Information technology — Artificial intelligence
— General rules for trustworthiness of AI systems

| GB/T 47507-2026 Requirement | DPP-CQ Implementation | Conformity |
|---|---|---|
| AI transparency | Mandatory `aiDisclosure` in credential (§4 of credential-formats.md) | ✅ Full |
| Human oversight | Final grading decision MUST be made by qualified human assessor | ✅ Full |
| Traceability of AI decisions | `methodologyReference` and `reportReference` URIs provide audit trail | ✅ Full |
| Reliability | AI assessment results are one input; human reviewer validates | ✅ Full |
| Privacy | AI processing follows data lifecycle governance (§8.3 of white paper) | ✅ Full |

**Declaration**: ICO declares that DPP-CQ v2.0's AI transparency provisions
conform to GB/T 47507-2026's requirements for AI systems used in quality
assessment.

**Limitations**: This declaration covers the standard's provisions only.
Individual implementations must ensure their specific AI systems comply.

## 4. EU AI Act (Regulation 2024/1689) — Article 50

**Framework**: EU Artificial Intelligence Act, Regulation (EU) 2024/1689,
Article 50 — Transparency obligations

| EU AI Act Art. 50 Requirement | DPP-CQ Implementation | Conformity |
|---|---|---|
| AI system disclosure | `aiDisclosure.aiUsed` mandatory flag | ✅ Full |
| AI role description | `aiDisclosure.aiRoles` enumerates specific functions | ✅ Full |
| Human oversight statement | `aiDisclosure.humanOversight` + `finalDecisionBy` | ✅ Full |
| Content authenticity | Credential provenance chain provides content origin | ✅ Aligned |

**Declaration**: ICO declares that DPP-CQ v2.0's AI transparency provisions
are aligned with the direction and intent of EU AI Act Article 50. DPP-CQ
exceeds minimum requirements by mandating disclosure (not merely "best effort")
and requiring retrievable methodology references.

**Limitations**: This declaration covers the standard's data model provisions.
Deployers must assess whether their use of AI in quality assessment triggers
additional obligations (e.g., high-risk classification under Art. 6).

## 5. EU ESPR / EN Standards

**Framework**: Regulation (EU) 2024/1781 (ESPR) and harmonized standards
EN 18219–18223 series

| Requirement | DPP-CQ Implementation | Conformity |
|---|---|---|
| Open data carrier (ESPR Art. 9) | Open carrier principle (§4 of carrier-specification.md) | ✅ Full |
| No proprietary app required | Open carrier principle, L1 QR readable by any smartphone | ✅ Full |
| Identifier interoperability | GTIN alongside DID; GS1 Digital Link URI | ✅ Full |
| Sustainability data attributes | Optional sustainability module (ISO 14067 PCF) | ✅ Aligned |
| EN 18220 core data attributes | Dual-dimension model; quality + sustainability | ✅ Aligned |

**Declaration**: ICO declares that DPP-CQ v2.0's carrier, identifier, and
data model provisions are fully aligned with ESPR Art. 9 and baseline-compatible
with the EN 18219–18223 series.

**Strategic note**: DPP-CQ's flagship categories (tea, wine & spirits, cultural
crafts, traditional medicine, specialty agri-foods) are not within the first
ESPR priority product groups. The standard has a strategic window to mature
its interop profile before statutory DPP obligations potentially reach its
categories.

## 6. GDPR (EU) & PIPL (China)

**Framework**: General Data Protection Regulation (EU) 2016/679; Personal
Information Protection Law (China)

| Requirement | DPP-CQ Implementation | Conformity |
|---|---|---|
| Data minimization | Selective disclosure (BBS+ / SD-JWT); verifiers receive only authorized claims | ✅ Full |
| Purpose limitation | `dataLifecycle` metadata specifies purpose and retention | ✅ Full |
| Storage limitation | `dataLifecycle.retentionPolicy` with deletion/anonymization rules | ✅ Full |
| Cross-border transfer | "Data localization, hash cross-border" architecture (§8.1 of white paper) | ✅ Full |
| Data subject rights | `dataLifecycle.privacyNoticeUri` provides rights information | ✅ Full |
| Privacy by design | Raw data stored locally; only hashes cross borders | ✅ Full |
| Consent management | Artisan personal data classified as Restricted (R) in disclosure classification | ✅ Full |

**Declaration**: ICO declares that DPP-CQ v2.0's data architecture and
disclosure mechanisms are designed to support conformity with both GDPR and
PIPL. The "data localization, hash cross-border" architecture fundamentally
reduces cross-border data compliance risks.

**Limitations**: Conformity depends on implementation. ICO provides the
framework; individual deployers must conduct their own DPIA/PIA for specific
use cases. See `docs/compliance/pia-summary.md` for the public PIA summary.

## 7. ISO Standards

| Standard | Scope | DPP-CQ Reference |
|---|---|---|
| ISO 14067:2018 | Carbon footprint of products | Sustainability module (`sustainability.pcf`) |
| ISO 22000:2018 | Food safety management | Referenced in supply chain traceability |
| ISO 22739:2021 | NFC and RFID standards | Carrier specification (L2/L3 NFC) |
| ISO 8601 | Date and time format | All date fields in the schema |
| ISO 3166-1 | Country codes | `origin.country` field |

## 8. Multilateral Standards

| Standard / Protocol | Scope | DPP-CQ Reference |
|---|---|---|
| W3C DID Core v1.1 | Decentralized identifiers | `did:ico:dpp` method |
| W3C VC Data Model v2.0 | Verifiable credentials | Core credential structure |
| IETF RFC 9529 | SD-JWT VC | SD-JWT credential format profile |
| GS1 Digital Link 2.2 | Supply chain identifiers | URI structure and resolver behavior |
| GS1 EPCIS 2.0 | Event data for supply chain | Event mapping (§4 of gs1-digital-link-mapping.md) |
| UN/CEFACT UNTP | UN Transparency Protocol | Conformity claims vocabulary |

---

*Part of ICO Std 2001:2026 (DPP-CQ v2.0.0-draft) · © 2026 International Communication Organization (ICO)*
*Licensed under CC BY 4.0*
