# Credential Format Profiles — SD-JWT VC, Data Integrity & National Cryptography

**ICO Std 2001 — Credential Format Annex (Normative)**
**Version:** v2.0.0-draft · **Status:** Public Review Draft · **Date:** 2026-08

> Defines the supported digital credential formats and cryptographic suites for
> DPP-CQ v2.0. Based on W3C Verifiable Credentials Data Model v2.0, IETF
> SD-JWT (RFC 9529) / SD-JWT VC, and W3C Data Integrity proofs. National
> cryptography options are defined for deployments under Chinese regulation.

---

## 1. Two Supported Profiles

DPP-CQ v2.0 supports **two normative credential profiles**. Issuers choose per
deployment; both express the same data model (`schemas/dpp-cq.schema.json`).

| | Profile A: JSON-LD + Data Integrity | Profile B: SD-JWT VC |
|---|---|---|
| **Format** | W3C VC v2.0 JSON-LD | IETF SD-JWT VC (RFC 9529 + SD-JWT VC draft) |
| **Selective disclosure** | BBS+ signatures (unlinkable) | SD-JWT disclosures (salted hashes) |
| **Proof type** | `DataIntegrityProof` (cryptosuite `bbs-2023` / `eddsa-2022`); legacy `BbsBlsSignature2020` | Compact JWS envelope (RFC 9529); JSON-LD form uses `DataIntegrityProof` with cryptosuite `ecdsa-sd-2023` |
| **Typical suite** | bbs-2023; Ed25519 (eddsa-2022) | ecdsa-sd-2023 (P-256) |
| **Strengths** | Rich JSON-LD semantics; unlinkable multi-show | Compact JWT; broad wallet/library support; IETF standard |
| **Recommended for** | Cross-border semantic interop, EPCIS/linked-data contexts | Mobile wallets, EU EUDI ecosystem, high-volume issuance |

Interop requirement: a DPP-CQ resolver **MUST** verify at least one profile and
**SHOULD** verify both. Root Resolver Network nodes verify both.

## 2. Selective Disclosure

- DPP-CQ v1.x specified Zero-Knowledge Proofs generically. v2.0 normalizes this
  to **standards-based selective disclosure**:
  - **BBS+** (Profile A): unlinkable derived credentials — holders can derive
    multiple unlinkable presentations from one credential (privacy-preserving
    repeat verification).
  - **SD-JWT** (Profile B): holder releases only the salted disclosures chosen
    for a verifier; undisclosed claims remain hidden while the signature stays
    valid.
- Fields **MUST** be classifiable per disclosure sensitivity:

| Class | Examples | Default disclosure |
|---|---|---|
| Public | Product name, category, quality grade, GI number | Revealed on consumer scan |
| Business-sensitive | Exact supplier pricing, detailed process params | Disclosed only to authorized verifiers |
| Personal | Artisan names, assessor identities | Disclosed only with consent / ZKP predicate |
| Integrity-anchored | Hash anchors, timestamps, status lists | Always verifiable, content not necessarily revealed |

## 3. Cryptographic Suites

### 3.1 International suites (default)

| Suite identifier | Algorithm | Standard |
|---|---|---|
| `eddsa-2022` | Ed25519 signatures | RFC 8032; Data Integrity eddsa-2022 |
| `ecdsa-sd-2023` | ECDSA P-256 + SD-JWT selective disclosure | SD-JWT VC / W3C VC-DI |
| `bbs-2023` | BBS+ signatures (BLS12-381) | W3C VC-DI BBS cryptosuite draft |

Hash function: SHA-256 (and SHA-384 where suite requires).

### 3.2 SM2/SM3/SM4 regional cryptography suite (optional, opt-in)

For deployments within jurisdictions where Chinese commercial cryptography
(商用密码) requirements apply, DPP-CQ defines the optional, region-scoped
suite **`sm2-with-sm3-2026`**. It is a deployment option alongside the
default international suites, never a normative baseline for cross-border
credentials:

| Function | Algorithm | Standard |
|---|---|---|
| Digital signature | SM2 (elliptic curve) | GB/T 32918 |
| Hash digest | SM3 | GB/T 32905 |
| Symmetric payload encryption (where needed) | SM4 | GB/T 32907 |

Rules:

1. The SM suite is **opt-in and region-scoped**: a credential signed with SM2
   **MUST** declare its suite in `proof.cryptosuite` (`sm2-with-sm3-2026`);
   root nodes outside the requiring jurisdiction are not required to verify
   SM2. The v1.x property name `cryptoSuite` is accepted on legacy credentials.
2. Cross-border credentials **SHOULD** use international suites; a dual-signature
   (SM2 for the requiring jurisdiction + Ed25519/ECDSA for international) MAY be attached via
   `proof.previousProof` chaining or parallel proof blocks in future minor
   versions.
3. SM3 hashes MAY anchor into domestic-compliant chains; the multi-chain
   abstraction layer (White Paper §7.3) already supports jurisdiction-specific
   anchoring.

## 4. Credential Status & Revocation

- Status lists use **BitstringStatusList** (W3C VC v2.0 standard), superseding
  the legacy RevocationList2020 mention in examples.
- W3C JSON-LD credentials carry Data Integrity proofs: the `proof` object uses
  `type: "DataIntegrityProof"` with the suite in property `cryptosuite`
  (lowercase, per W3C Data Integrity). Legacy suites (`BbsBlsSignature2020`,
  `Ed25519Signature2020`) remain verifiable. SD-JWT VC as a *compact
  serialization* (RFC 9529: `JWT~disclosures~signature`) is the transport
  envelope for wallet exchange; when represented as JSON-LD inside the DPP-CQ
  data model it uses the same `DataIntegrityProof`/`ecdsa-sd-2023` form.
- Revocation **MUST** propagate to all carrier resolution paths (QR and NFC)
  within the resolver's stated SLA (target: < 5 minutes).

## 5. Validity Fields

v2.0 accepts both legacy and W3C VC v2.0 canonical validity terms:

- `issuanceDate` (legacy) ≡ `validFrom` (v2.0)
- `expirationDate` (legacy) ≡ `validUntil` (v2.0)

New issuances **SHOULD** use `validFrom` / `validUntil`; both remain valid for
v1.x backward compatibility.

## 6. References

- W3C Verifiable Credentials Data Model v2.0 (W3C Recommendation, 2025)
- IETF RFC 9529 — SD-JWT: Selective Disclosure for JWTs (2024)
- IETF SD-JWT VC draft (SD-JWT-based Verifiable Credentials)
- W3C Data Integrity EdDSA / BBS cryptosuite specifications
- GB/T 32918 (SM2), GB/T 32905 (SM3), GB/T 32907 (SM4) — Chinese national
  commercial cryptography standards
