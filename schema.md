---
layout: page
title: "JSON Schema Reference"
permalink: /schema.html
---

# DPP-CQ JSON Schema Reference

> **ICO Std 2001-2026** — Core data schema for cultural and quality product digital passports.
> Based on W3C Verifiable Credentials Data Model v2.0.

**Schema ID:** `https://icoun.org/schemas/dpp-cq/v2.0.0-draft`
**JSON Schema dialect:** Draft 2020-12
**Document version:** v2.0.0-draft (Public Review Draft, 2nd round)

> This page summarizes the v2.0 data model. The machine-readable normative
> source is [`schemas/dpp-cq.schema.json`](https://github.com/ICO-cloud/dpp-cq-standard/blob/main/schemas/dpp-cq.schema.json).
> Every v2.0 addition is **OPTIONAL**; v1.x credentials remain valid.

---

## Top-Level Required Fields

| Field | Type | Description |
|-------|------|-------------|
| `@context` | `array[uri]` | Must include `https://www.w3.org/ns/credentials/v2` + the DPP-CQ context |
| `type` | `array[string]` | Must include `VerifiableCredential` + at least one DPP-CQ type |
| `issuer` | `string (uri)` | Issuer DID, e.g. `did:ico:issuer:<namespace>` |
| `issuanceDate` | `string (datetime)` | RFC 3339 issuance timestamp (v1.x term; `validFrom` accepted in v2.0) |
| `credentialSubject` | `object` | The product and its attributes (see below) |
| `proof` | `object` | Digital proof / signature |

## Top-Level Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string (uri)` | Credential ID, recommended `did:ico:dpp:<ns>:<id>` |
| `validFrom` / `validUntil` | `string (datetime)` | W3C VC v2.0 validity terms (≡ `issuanceDate` / `expirationDate`) |
| `expirationDate` | `string (datetime)` | v1.x expiry term, still accepted |
| `credentialStatus` | `object` | BitstringStatusList revocation/suspension entry |
| `conformityClaims` | `array` | **[v2.0]** UNTP-style self-declared conformity claims (framework, claim, conformity, evidence) |

---

## credentialSubject

### Required

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string (uri)` | Product DID |
| `productName` | `object` | Multilingual name (ISO 639-1 keys) |
| `category` | `string (enum)` | Product category code |

### Category Enum (v2.0)

`geographical-indication-tea` · `intangible-cultural-heritage-ceramic` ·
`haute-couture-apparel` · `geographical-indication-food` · `handicraft` ·
`specialty-agricultural-product` · `cultural-creative-product` ·
**`wine-and-spirits`** · **`traditional-medicine-health`** ·
**`light-consumer-goods`** · `other`

### Product-Level Objects

| Field | Version | Description |
|-------|---------|-------------|
| `gs1Identifiers` | **[v2.0]** | GS1 global identifiers (optional interop profile): `gtin` (valid mod-10 check digit required), `batchOrLot` (AI 10), `serialNumber` (AI 21), `glnOwner` (13-digit GLN), `digitalLink` (GS1 Digital Link URI, e.g. `https://id.gs1.org/01/06901234000016/10/.../21/...`) |
| `qualityGrade` | v1.0 | Quality grade per the issuing authority |
| `productImage` | v1.0 | IPFS CID or HTTPS URI |
| `origin` | v1.0 | Origin object: `type`, `country` (ISO 3166-1 alpha-2, required), `giNumber`, `region`, `coordinates` |
| `culturalData` | v1.0 | Heritage status/year/number, craft method/history, artisan info (with consent), cultural narrative |
| `traceability` | v1.0 | Harvest date, batch, supply-chain steps; **[v2.0]** each step MAY carry an `epcisEvent` mapping (EPCIS 2.0 event type, CBV 2.0 bizStep, action, event URI) |
| `qualityAttributes` | v1.0 | Sensory attributes, specifications (with **[v2.0]** `testStandard`), third-party attestations, and **[v2.0]** `assessment` disclosure (method, standard, assessor DID, date, report reference, `aiDisclosure`) |
| `sustainabilityData` | **[v2.0]** | Optional module: `carbonFootprint` (value, unit, functional unit, ISO 14067 method, boundary, verifier), `materials` (material, %, recycled content, hazardous), `endOfLife` |
| `dataLifecycle` | **[v2.0]** | Governance metadata: data controller, retention policy, storage jurisdiction, `crossBorderMode` (`hash-only` default / SCC / adequacy / local-only), deletion policy, privacy notice URI, PIA report URI |
| `authenticityMarks` | v1.0 | Physical anti-counterfeiting features; **[v2.0]** adds `carrierLevel` (`L1-open-qr` / `L2-sdm-nfc` / `L3-tamper-evident-nfc` / `physical-only`) and `specification` (standard, chip model, SDM flag, QR grade per ISO/IEC 15415, open-readability flag) |

### qualityAttributes.assessment.aiDisclosure (v2.0)

Required when assessment `method` is `ai-assisted` or `hybrid`:

- `aiAssisted` (`boolean`, must be `true`)
- `tasksPerformed` — list of AI tasks (e.g. data extraction, pre-scoring)
- `humanOversight.finalDecisionMadeBy` (required) — role of the human making the final grading decision
- `modelInfo` — model/version or vendor description (optional)

Aligned with EU AI Act Art. 50 transparency direction and GB/T 47507-2026.

---

## proof Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `type` | `string` | ✅ | `DataIntegrityProof` (current), or legacy `BbsBlsSignature2020` / `Ed25519Signature2020` |
| `cryptosuite` | `string` | — | **[v2.0]** W3C Data Integrity cryptosuite: `ecdsa-sd-2023` (SD-JWT-based selective disclosure), `eddsa-2022`, `bbs-2023`, or `sm2-with-sm3-2026` (domestic CN deployments) |
| `created` | `datetime` | ✅ | Proof creation timestamp |
| `proofPurpose` | `string (enum)` | ✅ | `assertionMethod` / `authentication` / `controllerProof` |
| `verificationMethod` | `string (uri)` | ✅ | DID key reference |
| `proofValue` | `string` | — | Signature value |

Notes:

- The v1.x property name `cryptoSuite` is accepted on legacy credentials; new issuances use `cryptosuite` (per W3C Data Integrity).
- SD-JWT VC (RFC 9529) compact serialization (`JWT~disclosures~signature`) is the wallet transport envelope; when represented in this JSON-LD model it appears as a `DataIntegrityProof` with cryptosuite `ecdsa-sd-2023`. Full rules: [`docs/specs/credential-formats.md`](docs/specs/credential-formats.md).
- SM4 (GB/T 32907) applies to payload encryption, not signatures.

---

## Full Schema

📄 [dpp-cq.schema.json](https://github.com/ICO-cloud/dpp-cq-standard/blob/main/schemas/dpp-cq.schema.json)

```
Schema:     https://icoun.org/schemas/dpp-cq/v2.0.0-draft
Standard:   ICO Std 2001-2026
Version:    v2.0.0-draft (Public Review Draft)
License:    CC BY 4.0 (documentation) / Apache 2.0 (implementation)
```
