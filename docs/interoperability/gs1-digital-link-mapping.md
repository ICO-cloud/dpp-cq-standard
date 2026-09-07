# GS1 Digital Link & Identifier Mapping
## Normative Annex — ICO Std 2001 v2.0

> **Status**: Normative · Part of ICO Std 2001:2026 (DPP-CQ v2.0)
> **Maintained at**: `docs/interoperability/gs1-digital-link-mapping.md`
> **Version**: 2.0.0-draft

---

## 1. Scope

This annex defines how DPP-CQ credentials interoperate with the GS1 identification
and Digital Link ecosystem. It is mandatory for all credentials issued under the
GS1 interop profile described in the white paper (§8.2b).

## 2. Identifier Binding Rules

### 2.1 GTIN ↔ DID Binding

Every DPP-CQ credential in the GS1 interop profile **MUST** carry both a GS1
Global Trade Item Number (GTIN) and a DPP-CQ Decentralized Identifier (DID).

| Identifier | Role | Format | Governance |
|---|---|---|---|
| GTIN-14 | Trade item identification (global supply chain) | 14-digit numeric (GS1 General Specifications) | GS1 Member Organisation |
| DID | Credential identity & resolution | `did:ico:dpp:<namespace>:<unique-id>` | ICO |

**Binding rules:**

1. A single GTIN **MAY** map to multiple DIDs (e.g., per-batch credentials for
   the same trade item).
2. Each DID **MUST** resolve to exactly one GTIN via the `gs1DigitalLink`
   property in the credential.
3. The binding **MUST** be recorded in the credential's `gs1DigitalLink` object:

```json
{
  "gs1DigitalLink": {
    "gtin": "06141411234567",
    "did": "did:ico:dpp:tea:longjing-xh-2026-001",
    "identifierRelation": "one-to-many"
  }
}
```

### 2.2 DID Format

The DPP-CQ DID uses the `did:ico:dpp` method name:

```
did:ico:dpp:<namespace>:<unique-id>
```

- `namespace`: Product category namespace (e.g., `tea`, `wine`, `ceramic`)
- `unique-id`: Product unique identifier; UUID v4 recommended for global
  uniqueness, or GS1-compatible coding for supply-chain alignment

### 2.3 Multi-Issuer Scenarios

When multiple entities issue credentials for the same product (e.g., producer
DPP + certifier quality credential), each issuer generates its own DID and
credential. The `gs1DigitalLink.gtin` field links them to the same trade item.

## 3. Digital Link URI Structure

### 3.1 URI Template

The GS1 Digital Link URI **MUST** follow this structure:

```
https://<resolver-domain>/{GTIN}
```

Where `<resolver-domain>` is the issuer's or a third-party GS1 Digital Link
resolver (e.g., `https://id.gs1.org/01/06141411234567`).

### 3.2 Content Negotiation

The resolver **MUST** support content negotiation per the GS1 Digital Link
standard (GS1 GS1 2.2):

| `Accept` Header | Response |
|---|---|
| `text/html` | Human-readable product information page (verification result) |
| `application/ld+json` | JSON-LD representation of the DPP-CQ credential |
| `application/vc+ld+json` | Verifiable Credential (JSON-LD, BBS+ proof) |
| `application/vc+sd-jwt` | SD-JWT VC representation |
| `application/json` | Simplified JSON summary |

### 3.3 Resolver Behavior

1. **Resolution**: The resolver receives a Digital Link URI, extracts the GTIN,
   and queries the ICO resolver API for the associated DID and credential hash.
2. **Presentation**: Based on the `Accept` header, the resolver returns the
   appropriate representation.
3. **Verification**: The resolver **MUST** verify credential validity (status
   check against the status list) before returning the credential data.
4. **Caching**: Resolved credentials **MAY** be cached for up to 24 hours;
   invalidation **MUST** occur upon revocation.

### 3.4 Link Header (RFC 8288)

The resolver **SHOULD** include `Link` headers pointing to related resources:

```
Link: <https://resolver.icoun.org/v1/did/did:ico:dpp:tea:longjing-xh-2026-001>; rel="canonical"
Link: <https://resolver.icoun.org/v1/credential/status>; rel="status"
```

## 4. EPCIS 2.0 Event Mapping

DPP-CQ credentials **MAY** be complemented by EPCIS 2.0 (Electronic Product
Code Information Services) events for granular supply chain traceability.

### 4.1 Event Types

| EPCIS Event | DPP-CQ Mapping | Notes |
|---|---|---|
| `ObjectEvent` | `credentialSubject.traceability.supplyChainSteps[]` | Harvest, processing, packaging |
| `AggregationEvent` | `credentialSubject.traceability.aggregation` | Pallet/case grouping |
| `TransactionEvent` | `credentialSubject.traceability.transaction` | Sale, transfer of ownership |
| `TransformationEvent` | `credentialSubject.traceability.transformation` | Processing that changes identity |

### 4.2 Event Structure

EPCIS events **MUST** reference the DPP-CQ credential DID in the `epcList` or
`childEPCs` field:

```json
{
  "type": "ObjectEvent",
  "action": "OBSERVE",
  "bizStep": "commissioning",
  "epcList": ["did:ico:dpp:tea:longjing-xh-2026-001"],
  "eventTime": "2026-03-28T06:00:00Z",
  "eventTimeZoneOffset": "+08:00",
  "readPoint": { "id": "urn:epc:id:sgln:0614141.00001.0" }
}
```

### 4.3 Storage & Access

- EPCIS events **SHOULD** be stored in a GS1-compliant EPCIS repository.
- The repository endpoint **MAY** be referenced in the credential via
  `credentialSubject.traceability.epcisEndpoint`.
- Access control **MUST** follow the same selective-disclosure principles as
  the credential itself (verifier receives only authorized events).

## 5. EN 18219 / EN 18220 Alignment

This annex aligns with the European standard series for digital product
passports:

| Standard | Scope | DPP-CQ Alignment |
|---|---|---|
| **EN 18219** | Data carriers for DPP — technical requirements | §3 Digital Link URI structure; open-carrier principle (§7.7 of white paper) |
| **EN 18220** | DPP data model — core data attributes | §2 identifier binding; §4 EPCIS mapping; dual-dimension model (quality + sustainability) |

### 5.1 Compliance Posture

DPP-CQ adopts a **"baseline compatibility, differentiated value"** posture:

- **Baseline compatibility (non-negotiable)**: open data carriers, global
  identifiers (GTIN alongside DID), standard credential formats (W3C VC /
  SD-JWT VC), standard APIs, and machine-readable conformity claims.
- **Differentiated value (independent)**: quality-and-culture assessment
  methodology (ICO Std 3001), multi-stakeholder governance, affordability
  for small producers, and applicability to cultural product categories
  that environmental DPPs do not cover.

## 6. Multilateral Bridge: UN/CEFACT UNTP

DPP-CQ's conformity claims vocabulary is aligned with the UN Transparency
Protocol (UNTP) to enable cross-jurisdiction interoperability through neutral,
multilateral standards rather than any single jurisdiction's registry.

| UNTP Concept | DPP-CQ Mapping |
|---|---|
| `conformityClaim` (UNTP) | `credentialSubject.qualityAttributes.certifications[]` |
| `facility` (UNTP) | `credentialSubject.traceability.supplyChainSteps[].location` |
| `product` (UNTP) | `credentialSubject` (product-level credential) |
| `process` (UNTP) | `credentialSubject.traceability.transformation` |

---

*Part of ICO Std 2001:2026 (DPP-CQ v2.0.0-draft) · © 2026 International Communication Organization (ICO)*
*Licensed under CC BY 4.0*
