# DPP-CQ Standards Conformity Declarations

**ICO Std 2001 — Compliance Document Set**
**Version:** v2.0.0-draft · **Date:** 2026-08

> This page hosts the DPP-CQ self-declarations of conformity against
> referenced regulatory and standards frameworks. Declarations describe the
> design-level alignment of the DPP-CQ specification; product-level conformity
> remains the responsibility of each issuer and is expressed per credential via
> `conformityClaims` (see JSON Schema v2.0). DPP-CQ is an open technical
> specification published by ICO; it is not a statutory certification scheme.
> Within the DPP-CQ system the terms used are assessment / evaluation /
> verification (评定 / 评价 / 验证), not statutory "certification (认证)".

---

## 1. Declaration against GB/T 47507-2026 《人工智能 可信赖 通则》

**Framework:** GB/T 47507-2026 *Artificial intelligence — Trustworthiness —
General rules* (issued 2026-04-30, effective 2026-08-01; SAC/TC 28).

GB/T 47507-2026 specifies general trustworthiness requirements for AI systems
(transparency, fairness, privacy protection, data security, traceability,
explainability, controllability, etc.). DPP-CQ applies AI in quality
assessment support and therefore aligns its **AI-assisted assessment**
provisions with the standard:

| GB/T 47507 dimension | DPP-CQ v2.0 provision | Alignment |
|---|---|---|
| Data security | Hash anchoring, multi-chain abstraction, data-lifecycle metadata (`dataLifecycle`) | High |
| Privacy protection | Selective disclosure (SD-JWT / BBS+), data minimization, hash-only cross-border mode | High |
| Traceability | Three-tier verification, BitstringStatusList, supply-chain event records (EPCIS-mappable) | High |
| Full-lifecycle management | `dataLifecycle` module: controller, retention, storage location, deletion policy | High |
| Transparency | `qualityAttributes.assessment.aiDisclosure` — mandatory disclosure when AI is used | High |
| Controllability (human oversight) | `aiDisclosure.humanOversight.finalDecisionMadeBy` — final grading decision by a human assessor | High |
| Fairness | Assessment methodology standardization (ICO Std 3001), multi-stakeholder governance; assessment bodies independent and conflict-of-interest controlled | Partial — methodology detail to expand in Std 3001 |
| Explainability | Assessment reports referenceable per credential (`reportReference`); scoring rationale documented in assessment files | Partial |

**Conclusion:** DPP-CQ v2.0 design covers approximately 80% of the
trustworthiness directions applicable to an AI-assisted product assessment
context. Remaining items (fairness evaluation methodology detail, PIA report
publication) are tracked as v2.0/v2.1 work items. DPP-CQ can be positioned as
a **vertical implementation of the standard's data-trustworthiness dimensions
for product quality data**.

## 2. Declaration against the EU ESPR / European DPP standards

**Frameworks:** Regulation (EU) 2024/1781 (ESPR); EN 18219/18220/18221/18222/
18223 (CEN-CENELEC JTC 24, 2026); battery passport under Regulation (EU)
2023/1542 (reference benchmark).

| Requirement | DPP-CQ v2.0 provision | Status |
|---|---|---|
| Unique product identifier (EN 18219) | DID + GTIN(+serial) dual binding | Aligned (interop profile) |
| Open, generally-readable data carrier (EN 18220; ESPR Art. 9) | L1 open QR (GS1 Digital Link) + L2 SDM NFC; any-reader resolution | Aligned |
| Data storage / access (EN 18221) | Hash anchoring + off-chain storage; resolver content negotiation | Partial — registry integration P1/P2 |
| Standardized API (EN 18222) | Root Resolver API + Digital Link link types | Partial — full EN API conformance P1 |
| Interoperability (EN 18223) | W3C VC v2.0, JSON-LD, SD-JWT VC; EPCIS mapping | Partial — EPCIS event API P1 |
| Sustainability data attributes | `sustainabilityData` module (ISO 14067 carbon footprint, materials, end-of-life) | Aligned at field level; ESPR delegated-act attribute lists per product class to be mapped as acts are adopted |
| Conformity claim exchange | `conformityClaims` modeled on UN/CEFACT UNTP vocabulary | Aligned with UNTP direction |

**Scope note:** DPP-CQ's flagship product categories (tea, wine & spirits,
cultural crafts, traditional medicine products, specialty agri-foods) are
**not within the first ESPR priority product groups** (textiles, furniture,
batteries, electronics, etc.), so statutory DPP obligations for these goods are
not yet in force. DPP-CQ's alignment is forward-looking and interoperability-
driven; it does not replace statutory CE conformity or ESPR obligations where
they apply.

## 3. Data protection & cross-border framework

- **GDPR (EU):** data minimization, selective disclosure, privacy notice at
  verification (`privacyNoticeURI`), DPIA summary publication
  (`piaReportURI`), purpose limitation by disclosure class.
- **PIPL / DSL / CSL (China):** raw data localization, hash-only cross-border
  default (`crossBorderMode: hash-only`), Chinese commercial cryptography
  suite option (SM2/SM3/SM4), retention and deletion rules.
- The "data localization, hash cross-border" architecture is designed to be
  compatible with both regimes simultaneously; a dedicated GDPR/PIPL dual-
  compliance white paper is a P1 deliverable.

## 4. AI Act awareness

For AI-assisted assessment, DPP-CQ adopts AI transparency obligations
analogous to Regulation (EU) 2024/1689 Art. 50 (AI-generated content
transparency) as baseline practice regardless of deployment jurisdiction:
mandatory `aiDisclosure`, human final decision, and assessor identification.
High-risk system classification analysis for automated quality grading is a
P2 work item.

---

*These declarations are maintained by the ICO Technical Secretariat and
updated with each standard release. Questions: info@icoun.org.*
