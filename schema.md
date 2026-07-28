---
layout: page
title: "JSON Schema Reference"
permalink: /schema.html
---

# DPP-CQ JSON Schema Reference

> **ICO Std 2001-2026** — Core data schema for cultural and quality product digital passports.
> Based on W3C Verifiable Credentials Data Model v2.0.

**Schema ID:** `https://icoun.org/schemas/dpp-cq/v1.0.0`
**Draft:** JSON Schema Draft 2020-12

---

## Required Fields

| Field | Type | Description |
|-------|------|-------------|
| `@context` | `array[uri]` | JSON-LD context. Must include W3C VC base + DPP-CQ context |
| `type` | `array[string]` | Must include `VerifiableCredential` + at least one DPP-CQ type |
| `issuer` | `string (uri)` | DID of issuing authority. Format: `did:ico:issuer:<namespace>` |
| `issuanceDate` | `string (datetime)` | RFC 3339 issuance timestamp |
| `credentialSubject` | `object` | Product and its attributes |
| `proof` | `object` | Digital proof (signature) |

## Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string (uri)` | Unique credential ID. Recommended: `did:ico:dpp:<ns>:<id>` |
| `expirationDate` | `string (datetime)` | RFC 3339 expiration (recommended for quality products) |
| `credentialStatus` | `object` | Revocation/suspension status mechanism |

---

## credentialSubject

### Required

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string (uri)` | Product DID |
| `productName` | `object` | Multilingual product name (ISO 639-1 keys) |
| `category` | `string (enum)` | Product category code |

### Category Enum Values

- `geographical-indication-tea`
- `intangible-cultural-heritage-ceramic`
- `haute-couture-apparel`
- `geographical-indication-food`
- `handicraft`
- `specialty-agricultural-product`
- `cultural-creative-product`
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
| `supplyChainSteps` | `array` | Chain of supply steps, each with `step`, `date`, `location`, `entity`, `certification` |

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
| `certifications` | `array` | Third-party certs: `certificationBody`, `certificationType`, `certificateNumber`, `validUntil` |

---

## authenticityMarks Array

| Field | Type | Description |
|-------|------|-------------|
| `type` | `string (enum)` | `nfc-chip` / `qr-code` / `hologram` / `watermark` / `security-thread` / `other` |
| `identifier` | `string` | Unique identifier for the mark |
| `description` | `string` | Description of the feature |

---

## proof Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `type` | `string` | ✅ | Recommended: `BbsBlsSignature2020`, `Ed25519Signature2020`, `DataIntegrityProof` |
| `created` | `datetime` | ✅ | Proof creation timestamp |
| `proofPurpose` | `string (enum)` | ✅ | `assertionMethod` / `authentication` / `controllerProof` |
| `verificationMethod` | `string (uri)` | ✅ | DID key reference |
| `proofValue` | `string` | — | Signature value |

---

## Full Schema

The complete JSON Schema file is available at:

📄 [dpp-cq.schema.json](https://github.com/ICO-cloud/dpp-cq-standard/blob/main/schemas/dpp-cq.schema.json)

```
Schema: https://icoun.org/schemas/dpp-cq/v1.0.0
Standard: ICO Std 2001-2026
Version: 1.0.0 (Draft)
License: CC BY 4.0 (documentation) / Apache 2.0 (implementation)
```
