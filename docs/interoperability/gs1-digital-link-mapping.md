# GS1 Digital Link & Identifier Interoperability Mapping

**ICO Std 2001 — Interoperability Annex (Normative for the GS1 interop profile)**
**Version:** v2.0.0-draft · **Status:** Public Review Draft · **Date:** 2026-08

> This annex defines how DPP-CQ identifiers and data carriers map to the GS1
> global identification system (GTIN, GLN, Digital Link) and to the EU DPP / EN
> identifier requirements. Compliance with this annex is OPTIONAL: DPP-CQ
> credentials without GS1 identifiers remain valid. Products intended for
> international retail, customs, or EU DPP data exchange **SHOULD** implement
> the GS1 interop profile.

---

## 1. Rationale

The EU ESPR (Regulation (EU) 2024/1781) and the European DPP standards
(EN 18219 unique identifier; EN 18220 data carrier) assume globally
unambiguous product identification. Retail supply chains, customs systems and
the emerging EU DPP registry ecosystem overwhelmingly use GS1 identification.

DPP-CQ's native identifier is the W3C DID (`did:ico:dpp:<namespace>:<id>`),
which provides cryptographic control and item-level granularity. GS1's GTIN
provides global trade-item recognition. These are **complementary, not
competing**: the DID identifies and secures the *credential*; the GTIN
identifies the *trade item* in global commerce. DPP-CQ therefore mandates a
**dual-identifier binding** for the interop profile.

## 2. Identifier Binding

### 2.1 Model

| Identifier | Standard | Granularity | Role in DPP-CQ |
|---|---|---|---|
| GTIN (+ serial/lot) | GS1 General Specifications | Trade item / item level | Global commerce & regulatory recognition |
| Product DID | W3C DID Core 1.0 | Item level | Credential subject id; cryptographic control |
| GLN | GS1 | Legal entity / location | Brand owner / responsible actor |

### 2.2 Binding rules

1. A product credential in the GS1 interop profile **MUST** contain
   `credentialSubject.gs1Identifiers.gtin` and the DID-based
   `credentialSubject.id`.
2. The DID document of the product (or the issuer's root binding record)
   **MUST** include a `gs1` verification relationship asserting the GTIN
   binding, signed by the party controlling the GLN (brand owner).
3. GTIN allocation **MUST** follow GS1 rules (licensed GS1 Company Prefix or
   valid single GTIN assignment). DPP-CQ does not itself allocate GTINs.
4. Item-level traceability **SHOULD** use GS1 AI (21) serial number or AI (10)
   batch/lot, carried inside the DID-unique credential.

## 3. GS1 Digital Link Resolution

GS1 Digital Link (standard GS1 URI syntax, current version 1.6) encodes GS1
identifiers into a resolvable HTTPS URL. DPP-CQ carriers in the interop
profile **SHOULD** encode a Digital Link URI so that **any standard smartphone
reader** (no proprietary app) resolves the product passport.

### 3.1 URI structure

```
https://<domain>/01/<GTIN>/10/<batch>/21/<serial>
```

Example:

```
https://id.gtin.info/06901234000017/10/XH20260328A01/21/SN-LJ-2026-00042
```

### 3.2 Resolution behavior

A Digital Link resolver for a DPP-CQ product **MUST** support content
negotiation (HTTP `Accept` header) and link types:

| Link type | Returns |
|---|---|
| `text/html` (default consumer scan) | Consumer verification page (human readable) |
| `application/vc+ld+json` / `application/vc` | The DPP-CQ verifiable credential |
| `application/ld+json` | JSON-LD product passport data |
| `application/epcis+json` | EPCIS 2.0 supply-chain event feed (where available) |

The resolver **SHOULD** redirect to or delegate resolution to the DPP-CQ Root
Resolver Network for credential authenticity checks, so that a GS1 scan and a
DPP-CQ scan converge on the same trust root.

## 4. EPCIS 2.0 Traceability Mapping

Supply-chain steps (`credentialSubject.traceability.supplyChainSteps`) **MAY**
carry an `epcisEvent` mapping object (see JSON Schema v2.0). Mapping guidance:

| DPP-CQ step | EPCIS 2.0 event type | Typical CBV bizStep |
|---|---|---|
| Harvest / production start | ObjectEvent | `commissioning` |
| Processing / transformation | TransformationEvent | `transforming` |
| Quality assessment | ObjectEvent | `inspecting` |
| Packing / aggregation | AggregationEvent | `packing` |
| Shipping | ObjectEvent | `shipping` |
| Receiving / import | ObjectEvent | `receiving` |

Full EPCIS 2.0 / CBV 2.0 conformance is a P1 target (EPCIS-compatible event
API); v2.0-draft defines the field-level mapping only.

## 5. EU DPP / EN standard alignment

| EN standard | Subject | DPP-CQ v2.0 position |
|---|---|---|
| EN 18219 | Unique identifier | GTIN(+serial) for interop; DID for credential — both carried |
| EN 18220 | Data carrier | Open QR (Digital Link) + SDM NFC; see `carrier-specification.md` |
| EN 18221 | Data storage | Hash anchoring + off-chain storage; mapping P1 |
| EN 18222 | API | Root Resolver API + Digital Link content negotiation |
| EN 18223 | Interoperability | VC/JSON-LD + SD-JWT VC; EPCIS mapping P1 |

## 6. References

- GS1 Digital Link Standard, URI Syntax, version 1.6 (GS1, 2024)
- GS1 EPCIS 2.0 (GS1 Standard, 2022) & CBV 2.0
- Regulation (EU) 2024/1781 (ESPR), Art. 9–10 (digital product passport)
- CEN-CENELEC JTC 24, EN 18219 / EN 18220 series (2026)
- W3C Decentralized Identifiers (DID) Core 1.0 (W3C Recommendation)
