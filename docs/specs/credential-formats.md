# Credential Format Profiles
## Normative Annex — ICO Std 2001 v2.0

> **Status**: Normative · Part of ICO Std 2001:2026 (DPP-CQ v2.0)
> **Maintained at**: `docs/specs/credential-formats.md`
> **Version**: 2.0.0-draft

---

## 1. Scope

This annex defines the two supported credential format profiles for DPP-CQ v2.0:
JSON-LD Data Integrity (BBS+) and SD-JWT VC. It also defines the selective
disclosure classification scheme and the optional Chinese national cryptography
suite.

## 2. Format Profiles

### 2.1 JSON-LD Data Integrity (BBS+)

**Specification**: W3C Verifiable Credentials Data Model v2.0 + Data Integrity
(BBS+ signature suite)

**Use case**: Selective disclosure of individual claims (field-level granularity);
unlinkable presentations.

#### Profile Requirements

| Property | Requirement |
|---|---|
| `@context` | MUST include `https://www.w3.org/ns/credentials/v2` and `https://icoun.org/contexts/dpp-cq/v1` |
| `type` | MUST include `VerifiableCredential` + at least one DPP-CQ type |
| `proof.type` | `DataIntegrityProof` (VC 2.0) or `BbsBlsSignature2020` (legacy) |
| `proof.cryptosuite` | `bbs-2023` (VC 2.0 Data Integrity) |
| `proof.proofPurpose` | `assertionMethod` |
| `proof.verificationMethod` | DID URL pointing to issuer's BBS+ public key |

#### Selective Disclosure

BBS+ enables the holder to derive a presentation containing only selected
claims. The verifier can verify the derived presentation without contacting
the issuer.

**Disclosure classification** (see §3 for full scheme):
- **Public claims**: Always disclosed (product name, grade, origin)
- **Holder-selectable claims**: Disclosed at holder's discretion (artisan info,
  detailed specifications)
- **Restricted claims**: Disclosed only to authorized verifiers (full supply
  chain, batch-level data)

#### Example (VC 2.0 Data Integrity)

```json
{
  "@context": [
    "https://www.w3.org/ns/credentials/v2",
    "https://icoun.org/contexts/dpp-cq/v1"
  ],
  "id": "did:ico:dpp:tea:longjing-xh-2026-001",
  "type": ["VerifiableCredential", "DPPQualityCredential"],
  "issuer": "did:ico:issuer:zjtea-assoc",
  "validFrom": "2026-07-15T00:00:00Z",
  "validUntil": "2027-07-14T23:59:59Z",
  "credentialSubject": { ... },
  "proof": {
    "type": "DataIntegrityProof",
    "cryptosuite": "bbs-2023",
    "created": "2026-07-15T10:30:00Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:ico:issuer:zjtea-assoc#keys-bbs-1",
    "proofValue": "u2V0..."
  }
}
```

### 2.2 SD-JWT VC (IETF RFC 9529)

**Specification**: IETF SD-JWT VC (RFC 9529) — Selective Disclosure for JWTs

**Use case**: Efficient credential presentation in mobile wallets; compact
serialization; widely supported by mobile platform wallets (Apple Wallet,
Google Wallet).

#### Profile Requirements

| Property | Requirement |
|---|---|
| Header `typ` | `vc+sd-jwt` |
| Header `alg` | `ES256` (ECDSA P-256) mandatory; `ES384` optional |
| Payload `vct` | `https://icoun.org/vct/dpp-cq/v1` (Verifiable Credential Type) |
| Payload `iss` | Issuer DID or HTTPS URL |
| Payload `cnf` | Holder binding (JWK or DID) |
| Payload `sd` | Array of salted digests for selectively disclosable claims |
| `_sd_alg` | `sha-256` (default) or `sha-384` |

#### SD-JWT Structure

```
<issuer-signed JWT>~<disclosure 1>~<disclosure 2>~...~<disclosure N>~<key binding JWT, optional>
```

Each disclosure is a base64url-encoded JSON array: `[salt, claim_name, claim_value]`

#### Example Disclosure

For the claim `"qualityGrade": "Premium Grade 1"`:
```
WyI5MjNkMzQ1NiIsICJxdWFsaXR5R3JhZGUiLCAiUHJlbWl1bSBHcmFkZSAxIl0
```

### 2.3 Format Selection Guidance

| Criterion | BBS+ (JSON-LD) | SD-JWT VC |
|---|---|---|
| Granularity | Field-level selective disclosure | Claim-level selective disclosure |
| Unlinkability | ✅ Unlinkable derived presentations | ⚠️ Issuer-signature JWT (linkable if not carefully managed) |
| Compactness | Larger (JSON-LD overhead) | Compact (JWT serialization) |
| Mobile wallet support | Limited (emerging) | Broad (Apple/Google Wallet) |
| Semantic interoperability | JSON-LD (RDF-based) | JWT claims (flat structure) |
| Recommended for | Regulatory / multi-party verification | Consumer-facing mobile flows |

**Interoperability**: Both formats resolve to the same semantic data model
(defined in `schemas/dpp-cq.schema.json`). A resolver MUST be able to serve
both formats for the same credential.

## 3. Disclosure Classification

DPP-CQ defines three disclosure classes for credential claims:

| Class | Label | Disclosure Rule | Examples |
|---|---|---|---|
| **P** | Public | Always disclosed in any presentation | Product name, category, quality grade, origin country, credential status |
| **H** | Holder-selectable | Disclosed at holder's discretion per presentation | Artisan name, detailed specifications, cultural narrative, supply chain steps |
| **R** | Restricted | Disclosed only to authorized verifiers (e.g., regulators, customs) | Batch-level data, full supply chain, laboratory results, personal data |

### 3.1 Default Classification

The following table provides default classifications. Issuers MAY elevate (but
not lower) the classification of specific claims:

| Claim | Default Class | Notes |
|---|---|---|
| `productName` | P | Core identification |
| `category` | P | Core identification |
| `qualityGrade` | P | Core quality claim |
| `origin.country` | P | Core origin |
| `origin.giNumber` | P | GI registration is public |
| `origin.region` | P | Core origin |
| `origin.coordinates` | H | May reveal precise location |
| `culturalData.heritageStatus` | P | Public classification |
| `culturalData.artisanInfo.name` | R | Personal data; requires consent |
| `culturalData.culturalNarrative` | H | Optional narrative |
| `traceability.batchNumber` | R | Batch-level operational data |
| `traceability.supplyChainSteps` | H | Holder decides granularity |
| `qualityAttributes.specifications` | H | Lab results may be competitive |
| `qualityAttributes.certifications` | P | Certifications are public record |
| `sustainability.*` | H | Holder decides disclosure scope |
| `aiDisclosure.*` | P | Transparency is mandatory (see §4) |
| `dataLifecycle.*` | P | Data governance transparency |

### 3.2 AI Disclosure (Mandatory)

Where AI systems support quality assessment, the credential **MUST** include:

```json
{
  "qualityAttributes": {
    "assessment": {
      "aiDisclosure": {
        "aiUsed": true,
        "aiRoles": ["data-extraction", "pre-scoring"],
        "humanOversight": true,
        "finalDecisionBy": "human-assessor",
        "methodologyReference": "https://resolver.icoun.org/methods/tea-premium-v3",
        "reportReference": "https://resolver.icoun.org/reports/XH20260328A01",
        "regulatoryBasis": ["GB/T 47507-2026", "EU AI Act Art.50"]
      }
    }
  }
}
```

**Rules:**
- `aiDisclosure` is **MANDATORY** if AI was used in any assessment step
- `aiDisclosure.aiUsed` **MUST** be `true` when AI participated
- The final grading decision **MUST** be made by a qualified human assessor
- The assessment methodology and full report **MUST** be retrievable via URI

## 4. Chinese National Cryptography Suite (Optional)

For deployments within mainland China or other jurisdictions requiring
national cryptography standards, DPP-CQ supports an optional SM2/SM3/SM4
cryptography suite.

### 4.1 Algorithm Mapping

| Function | International Default | Chinese Suite (Optional) | Standard |
|---|---|---|---|
| Digital Signature | Ed25519 / ES256 | SM2 | GB/T 32918 |
| Hash Function | SHA-256 | SM3 | GB/T 32905 |
| Symmetric Encryption | AES-128/256 | SM4 | GB/T 32907 |

### 4.2 Implementation

When the Chinese suite is selected:

1. **Signature**: `proof.type` = `DataIntegrityProof`, `proof.cryptosuite` =
   `sm2-2024`
2. **Hash**: All hash operations use SM3 instead of SHA-256
3. **Encryption**: All symmetric encryption uses SM4 instead of AES

### 4.3 Interoperability Note

Credentials signed with the Chinese suite **MUST** still be resolvable via
the standard DID document. The issuer's DID document **MUST** list both key
types:

```json
{
  "verificationMethod": [
    {
      "id": "did:ico:issuer:zjtea-assoc#keys-bbs-1",
      "type": "Bls12381G2Key2020",
      "controller": "did:ico:issuer:zjtea-assoc",
      "publicKeyMultibase": "z..."
    },
    {
      "id": "did:ico:issuer:zjtea-assoc#keys-sm2-1",
      "type": "SM2VerificationKey2024",
      "controller": "did:ico:issuer:zjtea-assoc",
      "publicKeyMultibase": "z..."
    }
  ]
}
```

## 5. Status & Validity Rules

### 5.1 Credential Status

Credentials **SHOULD** use the W3C BitstringStatusList (VC 2.0) for status
management:

```json
{
  "credentialStatus": {
    "id": "https://resolver.icoun.org/v1/status/001#42",
    "type": "BitstringStatusListEntry",
    "statusPurpose": "revocation",
    "statusListIndex": "42",
    "statusListCredential": "https://resolver.icoun.org/v1/status/001"
  }
}
```

### 5.2 Validity Period

- `validFrom` / `validUntil` (VC 2.0) or `issuanceDate` / `expirationDate`
  (VC 1.x legacy) **SHOULD** be set for all credentials
- Quality-sensitive products (food, tea) **MUST** have an expiration date
- Expired credentials **MUST** return status `expired` upon verification
- Revoked credentials **MUST** return status `revoked` with revocation reason

### 5.3 Revocation

- Revocation is performed by setting the corresponding bit in the status list
- Revocation **MUST** be performed by the issuer or an authorized revocation
  service
- Revoked credentials remain verifiable (signature is still valid) but return
  status `revoked`
- Revocation reason **SHOULD** be provided in the status list entry

---

*Part of ICO Std 2001:2026 (DPP-CQ v2.0.0-draft) · © 2026 International Communication Organization (ICO)*
*Licensed under CC BY 4.0*
