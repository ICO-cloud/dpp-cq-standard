---
layout: page
title: "JSON Schema Reference"
permalink: /schema.html
---

# DPP-CQ JSON Schema Reference

> **ICO Std 2001:2026** — Core data schema for cultural and quality product digital passports.
> Based on W3C Verifiable Credentials Data Model v2.0.

**Schema ID:** `https://icoun.org/schemas/dpp-cq/v2.0.0-draft`
**Draft:** JSON Schema Draft 2020-12
**Version:** 2.0.0-draft

---

## Required Fields

| Field | Type | Description |
|-------|------|-------------|
| `@context` | `array[uri]` | JSON-LD context. Must include W3C VC v2 base + DPP-CQ context |
| `type` | `array[string]` | Must include `VerifiableCredential` + at least one DPP-CQ type |
| `issuer` | `string (uri)` or `object` | DID string or `{id, name}` object |
| `validFrom` | `string (datetime)` | RFC 3339 issuance timestamp (VC 2.0). `issuanceDate` also accepted for v1.x compat |
| `credentialSubject` | `object` | Product and its attributes |
| `proof` | `object` | Digital proof (signature) |

## Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string (uri)` | Unique credential ID. Recommended: `did:ico:dpp:<ns>:<id>` |
| `validUntil` | `string (datetime)` | RFC 3339 expiration (VC 2.0). `expirationDate` also accepted for v1.x compat |
| `credentialStatus` | `object` | Revocation/suspension status mechanism |
| `termsOfUse` | `array` | Terms of use policies |

---

## credentialSubject

### Required

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string (uri)` | Product DID |
| `productName` | `object` or `string` | Multilingual product name (ISO 639-1 keys) or plain string |
| `category` | `string (enum)` | Product category code |

### Category Enum Values

- `geographical-indication-tea`
- `intangible-cultural-heritage-ceramic`
- `haute-couture-apparel`
- `geographical-indication-food`
- `handicraft`
- `specialty-agricultural-product`
- `cultural-creative-product`
- `traditional-medicine` *(new in v2.0)*
- `wine-and-spirits` *(new in v2.0)*
- `other`

### Optional Product Fields

| Field | Type | Description |
|-------|------|-------------|
| `qualityGrade` | `string` | Quality grade per issuing authority |
| `productImage` | `string (uri)` | IPFS CID or HTTPS URL |
| `origin` | `object` | Geographical origin (see below) |
| `culturalData` | `object` | Cultural heritage data (see below) |
| `traceability` | `object` | Supply chain traceability (see below) |
| `qualityAttributes` | `object` | Sensory and quality attributes (see below) |
| `authenticityMarks` | `array` | Physical anti-counterfeiting features |
| `sustainability` | `object` | *New in v2.0* — Environmental sustainability data (see below) |
| `carrierTier` | `object` | *New in v2.0* — Physical carrier classification (see below) |
| `gs1DigitalLink` | `object` | *New in v2.0* — GS1 Digital Link binding (see below) |
| `dataLifecycle` | `object` | *New in v2.0* — Data lifecycle governance (see below) |

---

## origin Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `type` | `string (enum)` | ✅ | `GeographicalIndication` / `PlaceOfOrigin` / `ManufacturingLocation` |
| `country` | `string` | ✅ | ISO 3166-1 alpha-2 code |
| `giNumber` | `string` | — | Official GI registration number |
| `region` | `string` | — | Region or place name |
| `coordinates` | `object` | — | `latitude` + `longitude` |

---

## culturalData Object

| Field | Type | Description |
|-------|------|-------------|
| `heritageStatus` | `string (enum)` | UNESCO ICH / National ICH / Provincial ICH / Traditional Craft / Culturally Significant / None |
| `heritageYear` | `integer` | Year of inscription |
| `heritageNumber` | `string` | Official registration number |
| `craftMethod` | `string` | Traditional craftsmanship description |
| `craftHistory` | `string` | Historical background |
| `artisanInfo` | `object` | Artisan details (with consent): `name`, `title`, `generation`, `biography` |
| `culturalNarrative` | `string` | Cultural story or significance |

---

## traceability Object

| Field | Type | Description |
|-------|------|-------------|
| `harvestDate` | `string (date)` | Harvest/production date (ISO 8601) |
| `processLocation` | `string` | Processing location |
| `batchNumber` | `string` | Production batch/lot number |
| `epcisEndpoint` | `string (uri)` | *New in v2.0* — EPCIS 2.0 endpoint URI |
| `supplyChainSteps` | `array` | Chain of supply steps, each with `step`, `date`, `location`, `entity`, `certification`, `epcisEventType` |

### epcisEventType Enum Values

- `ObjectEvent`
- `AggregationEvent`
- `AssociationEvent`
- `TransactionEvent`
- `TransformationEvent`

---

## qualityAttributes Object

| Field | Type | Description |
|-------|------|-------------|
| `appearance` | `string` | Visual characteristics |
| `aroma` | `string` | Scent profile |
| `taste` | `string` | Flavor profile |
| `texture` | `string` | Tactile qualities |
| `materialComposition` | `string` | Material breakdown |
| `specifications` | `array` | Technical specs: `attribute`, `value`, `unit`, `testMethod` |
| `certifications` | `array` | Third-party certs: `certificationBody`, `certificationType`, `certificateNumber`, `validUntil`, `conformityClaimRef` |
| `assessment` | `object` | *New in v2.0* — Quality assessment details (see below) |

### assessment Object (v2.0)

| Field | Type | Description |
|-------|------|-------------|
| `methodologyReference` | `string (uri)` | Reference to assessment methodology |
| `reportReference` | `string (uri)` | Reference to assessment report |
| `assessorRole` | `string` | Role/classification of assessor |
| `aiDisclosure` | `object` | AI involvement disclosure (see below) |

### aiDisclosure Object (v2.0)

| Field | Type | Description |
|-------|------|-------------|
| `aiUsed` | `boolean` | Whether AI was used in assessment |
| `aiRoles` | `array[string]` | Roles: `data-extraction`, `pre-scoring`, `pattern-recognition`, `grading-assistance`, `none` |
| `humanOversight` | `boolean` | Whether human oversight was applied |
| `finalDecisionBy` | `string` | Who made the final decision: `human` / `human-with-ai-assistance` |
| `methodologyReference` | `string (uri)` | AI methodology reference |
| `reportReference` | `string (uri)` | AI audit report reference |
| `regulatoryBasis` | `array[string]` | Regulatory frameworks: `EU-AI-Act-Art50`, `GB-T-47507-2026` |

---

## sustainability Object (v2.0)

| Field | Type | Description |
|-------|------|-------------|
| `carbonFootprint` | `object` | PCF data: `value`, `unit`, `standard` (ISO 14067), `scope` (cradle-to-gate/cradle-to-grave), `verified` |
| `materialComposition` | `array` | Materials: `material`, `percentage`, `origin`, `certified` |
| `endOfLife` | `object` | Disposal: `recyclable`, `recyclingRate`, `compostable`, `instructions` |
| `packaging` | `object` | Packaging: `type`, `recyclable`, `material`, `weight` |

---

## carrierTier Object (v2.0)

| Field | Type | Description |
|-------|------|-------------|
| `level` | `string (enum)` | `L1` / `L2` / `L3` |
| `primary` | `string (enum)` | Primary carrier: `open-qr`, `sdm-nfc`, `tamper-evident-nfc` |
| `secondary` | `string` | Secondary carrier (if dual-carrier) |
| `nfcChipType` | `string` | NFC chip model (e.g., `NTAG-424-DNA-TT`) |
| `tamperEvident` | `boolean` | Whether tamper-evident features are present |
| `dualCarrier` | `boolean` | Whether dual-carrier mode is active |

---

## gs1DigitalLink Object (v2.0)

| Field | Type | Description |
|-------|------|-------------|
| `gtin` | `string` | Global Trade Item Number (14-digit) |
| `did` | `string (uri)` | DID bound to this GTIN |
| `identifierRelation` | `string` | Relationship: `gtin-did-binding` |
| `digitalLinkUri` | `string (uri)` | GS1 Digital Link URI |

---

## dataLifecycle Object (v2.0)

| Field | Type | Description |
|-------|------|-------------|
| `controller` | `string` | Data controller name |
| `controllerContact` | `string` | Contact information |
| `retentionPolicy` | `string` | Data retention period |
| `storageJurisdiction` | `array[string]` | ISO country codes for storage locations |
| `crossBorderMode` | `string (enum)` | `full-replication` / `hash-only` / `no-cross-border` |
| `deletionRules` | `string` | Data deletion conditions |
| `privacyNoticeUri` | `string (uri)` | Link to privacy notice |
| `piaSummaryUri` | `string (uri)` | Link to privacy impact assessment summary |

---

## authenticityMarks Array

| Field | Type | Description |
|-------|------|-------------|
| `type` | `string (enum)` | `nfc-chip` / `qr-code` / `hologram` / `watermark` / `security-thread` / `sdm-nfc` / `tamper-evident-nfc` / `open-qr` / `other` |
| `identifier` | `string` | Unique identifier for the mark |
| `description` | `string` | Description of the feature |

---

## proof Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `type` | `string` | ✅ | Recommended: `DataIntegrityProof`, `BbsBlsSignature2020`, `Ed25519Signature2020` |
| `created` | `datetime` | ✅ | Proof creation timestamp |
| `proofPurpose` | `string (enum)` | ✅ | `assertionMethod` / `authentication` / `controllerProof` |
| `verificationMethod` | `string (uri)` | ✅ | DID key reference |
| `proofValue` | `string` | — | Signature value |
| `cryptosuite` | `string` | *New in v2.0* — e.g., `bbs-2023`, `eddsa-2022`, `ecdsa-sd-2023` |

---

## Full Schema

The complete JSON Schema file is available at:

📄 [dpp-cq.schema.json](https://github.com/ICO-cloud/dpp-cq-standard/blob/main/schemas/dpp-cq.schema.json)

```
Schema: https://icoun.org/schemas/dpp-cq/v2.0.0-draft
Standard: ICO Std 2001:2026
Version: 2.0.0-draft
License: CC BY 4.0 (documentation) / Apache 2.0 (implementation)
```
