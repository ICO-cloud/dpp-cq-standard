# DPP-CQ Standards Conformity Declarations

**ICO Std 2001 — Compliance Document Set**
**Version:** v2.0.0-draft · **Date:** 2026-09

> This page hosts the DPP-CQ self-declarations of conformity against
> referenced regulatory and standards frameworks. Declarations describe the
> design-level alignment of the DPP-CQ specification; product-level conformity
> remains the responsibility of each issuer and is expressed per credential via
> `conformityClaims` (see JSON Schema v2.0). DPP-CQ is an open technical
> specification published by ICO; it is not a statutory certification scheme.
> Within the DPP-CQ system the terms used are assessment / evaluation /
> verification (评定 / 评价 / 验证), not statutory "certification (认证)".
>
> **Scope of references:** DPP-CQ is an international standard. Its normative
> external references are international and regional open standards (W3C,
> IETF, ISO/IEC, ITU-T, EN). Section 4 below is an **informative jurisdiction
> deployment mapping** for deployments within China; it is not a normative
> reference of the standard and imposes no requirement on deployments outside
> that jurisdiction.

---

## 1. AI governance declaration — ISO/IEC 42001:2023 and EU AI Act Art. 50

**Frameworks:** ISO/IEC 42001:2023 *Artificial intelligence — Management
system* (AIMS); Regulation (EU) 2024/1689 Art. 50 (transparency obligations).

Where AI systems support quality assessment (data extraction, pre-scoring,
image recognition), DPP-CQ adopts its own transparency and human-oversight
rules, following the governance direction of ISO/IEC 42001 and obligations
analogous to EU AI Act Art. 50, as baseline practice regardless of deployment
jurisdiction:

| Governance dimension | DPP-CQ v2.0 provision |
|---|---|
| AI policy and accountability | AI use scoped to assessment *support*; issuer accountable per credential; multi-stakeholder governance oversees methodology |
| Transparency / disclosure | Mandatory `qualityAttributes.assessment.aiDisclosure` when the method is `ai-assisted` or `hybrid`; model/version information may be disclosed |
| Human oversight | `aiDisclosure.humanOversight.finalDecisionMadeBy` required — the final grading decision is made by a qualified human assessor |
| Data governance | `dataLifecycle` module: controller, retention, storage jurisdiction, cross-border mode, deletion policy; hash anchoring and multi-chain abstraction |
| Traceability | Three-tier verification, BitstringStatusList, EPCIS-mappable event records, per-credential report reference |
| Privacy | Selective disclosure (SD-JWT / BBS+), data minimization, hash-only cross-border default |
| Continual improvement | Fairness-evaluation methodology detail and PIA publication tracked as v2.0/v2.1 work items; high-risk classification analysis for automated grading is a P2 item |

**Conclusion:** DPP-CQ v2.0 implements the AIMS governance direction and
Art. 50-style transparency for the narrow context of AI-assisted product
quality assessment. This is a design-level self-declaration, not a statutory
certification and not a claim of ISO/IEC 42001 certification by any party.

## 2. Declaration against the EU ESPR / European DPP standards

**Frameworks:** Regulation (EU) 2024/1781 (ESPR); EN 18219/18220/18221/18222/
18223 (CEN-CENELEC JTC 24, 2026); battery passport under Regulation (EU)
2023/1542 (reference benchmark).

| Requirement | DPP-CQ v2.0 provision | Status |
|---|---|---|
| Unique product identifier (EN 18219) | DID + GTIN(+serial) dual binding | Aligned (interop profile) |
| Open, generally-readable data carrier (EN 18220; ESPR Art. 9) | L1 open QR (GS1 Digital Link) + L2 SDM NFC; any-reader resolution | Aligned |
| Data storage / access (EN 18221) | Hash anchoring + off-chain storage; resolver content negotiation | Partial — registry integration P1/P2 |
| Standardized API (EN 18222) | Open interoperability API (`docs/interoperability/api-specification.md`): Read/Lifecycle/Search levels; Root Resolver endpoints = Read subset | Read level normative; Lifecycle/Search implementation tracked for v2.0 stable |
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

## 4. Informative jurisdiction mapping — deployments within China

> **Status: informative, non-normative.** The following is deployment-support
> information for operators implementing DPP-CQ within mainland China. It is
> not a normative reference of the standard, does not modify the normative AI
> governance provisions in §1, and imposes no requirement on deployments
> elsewhere.

For operators subject to Chinese law, the DPP-CQ v2.0 provisions overlap
substantially with the trustworthiness directions of GB/T 47507-2026
(*Artificial intelligence — Trustworthiness — General rules*). The mapping
below is provided for convenience; the normative baseline for DPP-CQ's AI
provisions remains ISO/IEC 42001:2023 and EU AI Act Art. 50 (see §1).

| GB/T 47507 dimension | Corresponding DPP-CQ v2.0 provision | Overlap |
|---|---|---|
| Data security | Hash anchoring, multi-chain abstraction, data-lifecycle metadata (`dataLifecycle`) | High |
| Privacy protection | Selective disclosure (SD-JWT / BBS+), data minimization, hash-only cross-border mode | High |
| Traceability | Three-tier verification, BitstringStatusList, supply-chain event records (EPCIS-mappable) | High |
| Full-lifecycle management | `dataLifecycle` module: controller, retention, storage location, deletion policy | High |
| Transparency | `qualityAttributes.assessment.aiDisclosure` — mandatory disclosure when AI is used | High |
| Controllability (human oversight) | `aiDisclosure.humanOversight.finalDecisionMadeBy` — final grading decision by a human assessor | High |
| Fairness | Assessment methodology standardization (ICO Std 3001), multi-stakeholder governance; assessment bodies independent and conflict-of-interest controlled | Partial — methodology detail to expand in Std 3001 |
| Explainability | Assessment reports referenceable per credential (`reportReference`); scoring rationale documented in assessment files | Partial |

Regional cryptography: deployments required to use commercial cryptography
may select the optional SM2/SM3/SM4 suite (`sm2-with-sm3-2026`); it is an
opt-in profile alongside the default international suites.

High-risk system classification analysis for automated quality grading is a
P2 work item.

---

*These declarations are maintained by the ICO Technical Secretariat and
updated with each standard release. Questions: info@icoun.org.*
