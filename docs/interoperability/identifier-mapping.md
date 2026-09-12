# Identifier Interoperability — OID ↔ DID Compatibility Binding

**ICO Std 2001 — Identifier Annex (Normative)**
**Version:** v2.0.0-draft · **Status:** Public Review Draft · **Date:** 2026-09

> Defines how a DPP-CQ passport carries identifiers from **both** major
> international identifier architectures — the hierarchical Object Identifier
> (OID) system of ISO/IEC & ITU-T and the decentralized W3C Decentralized
> Identifier (DID) system — so that one credential can be resolved and
> cross-checked by registries, enterprise systems, and border/trade platforms
> built on either architecture. This is a **compatibility binding at the
> application layer**, not a new DID method and not a change to the
> `did:ico:dpp` root resolution mechanism.

---

## 1. Two International Identifier Architectures

| | OID | DID |
|---|---|---|
| Governing standards | ITU-T X.660 / ISO/IEC 9834-1 (registration tree & procedures); ASN.1 OID and OID-IRI defined in ITU-T X.680 / ISO/IEC 8824-1 | W3C *Decentralized Identifiers (DIDs) v1.0* (W3C Recommendation, 2022-07-19) |
| Structure | Hierarchical dotted-integer tree (`2.42.x.…`); an OID-IRI and the registered `urn:oid:` form carry the same value | URI of form `did:<method>:<method-specific-id>`, resolvable to a DID document |
| Administration | Registration Authorities allocate child arcs under X.660 / 9834-1; top arcs: 0 ITU-T, 1 ISO, 2 joint | Controllers create and manage identifiers; no central issuing agency |
| Strengths | Deep deployment in certificates, healthcare, telecom, enterprise and government registries; strong organizational lineage | Cryptographically verifiable control, decentralized, privacy-respecting, natively binds verification material and service endpoints |

Both are international, multi-jurisdiction systems. DPP-CQ treats them as
complementary: OID carries **organizational/registration lineage**, DID
carries **cryptographic control and verifiability**.

## 2. Design Position

1. **DID remains the canonical product identifier** for DPP-CQ credentials and
   the Root Resolver. This annex does not replace `did:ico:dpp`, and does not
   require OID for any deployment.
2. **No new DID method is registered.** `did:oid:` is intentionally **not**
   introduced. A new method would require an independent specification and
   resolution network; equivalence is instead expressed with standard,
   already-supported DID document and credential mechanisms.
3. **Binding is opt-in and one-to-one.** An issuer that holds (or whose
   registration authority holds) a valid OID arc MAY bind that OID to a
   product/issuer DID. The mapping is a claim of **same-subject equivalence**,
   not a re-issuance.
4. **No fabricated allocations.** ICO does not mint OID numbers. An OID
   referenced in a credential **MUST** be a value officially allocated by an
   X.660 / 9834-1 Registration Authority. ICO neither issues OID arcs nor
   asserts allocation authority; organizations obtain arcs through their
   member-body or International Registration Authority channel.

## 3. Binding Mechanisms (Normative)

Two mechanisms are defined; implementations **MUST** support mechanism M1, and
**MAY** additionally use M2.

### M1 — DID document `alsoKnownAs` + credential alias property

The issuer's or product's DID document lists the equivalent identifier using
the standard W3C DID Core `alsoKnownAs` property, in the registered OID URN
form (RFC 3061 `urn:oid:`):

```json
{
  "id": "did:ico:dpp:tea:longjing-xh-2026-001",
  "alsoKnownAs": [
    "urn:oid:2.42.12345.67.001"
  ],
  "verificationMethod": [ "…" ],
  "service": [ "…" ]
}
```

The DPP-CQ credential record **MUST** carry the same equivalence in a structured
field so that non-DID enterprise systems can read it without resolving a DID
document:

```json
"identifiers": {
  "canonicalDid": "did:ico:dpp:tea:longjing-xh-2026-001",
  "alias": [
    { "scheme": "gtin", "value": "06901234000017" },
    { "scheme": "oid",  "value": "urn:oid:2.42.12345.67.001" }
  ]
}
```

(`2.42.…` is illustrative only; a real credential carries an allocated value.)

### M2 — OID-IRI resolution redirect

Where an OID resolution/repository service exposes OID-IRI or `urn:oid:`
resolution, the OID record's descriptive metadata **MAY** point back to the
DPP-CQ resolver/passport URI. This keeps the OID-side registry authoritative
for lineage while the passport remains the source of product/quality data.
DPP-CQ resolvers **MUST** accept inbound lookups keyed by `urn:oid:` through
the open search API (`GET /identifiers/oid/{oid}`, see
`api-specification.md` §4.2) and redirect to the bound passport when a
binding exists.

## 4. Resolution and Verification Flow

```
Lookup by either identifier
        │
        ├── DID input → resolve DID document → read alsoKnownAs → obtain OID
        │
        └── OID input (urn:oid / dotted form)
                → DPP-CQ /identifiers/oid/ search
                → canonical product DID
        │
        ▼
Verify credential signature & status on the canonical DID
        │
        ▼
Cross-check: bound OID is (a) formally allocated and
(b) matches an active DID-document binding
```

A binding is accepted only when **both directions agree**: the DID document
cites the OID **and** the presented passport record cites the same OID for
the same subject. A mismatch, an unallocated OID, or a one-sided claim
**MUST** be surfaced as an identifier-consistency warning, never silently
normalized.

## 5. Rules

1. The OID value **MUST** be expressed in the credential in canonical
   `urn:oid:` form; dotted-decimal and OID-IRI are accepted on input and
   normalized.
2. Bindings are immutable per credential version; rebinding after a
   revocation or ownership transfer produces a new credential version and a
   new hash anchor.
3. The mapping layer does not alter the hash-cross-border architecture,
   selective-disclosure model, or carrier requirements.
4. OID equivalence is an **identity/lineage** claim; it conveys no quality
   result and no conformity assessment outcome by itself.
5. Deployments that do not use OID are unaffected; the canonical DID path is
   self-sufficient.

## 6. Why This Matters

A passport readable through both architectures can move through:
W3C/verifiable-credential ecosystems and EUDI-style wallets **and**
certificate-, EDI-, and registry-based enterprise/government systems that
speak OID/ASN.1. DPP-CQ therefore bridges two international identifier worlds
at the application layer without subordinating either to a single national
scheme, and without changing its independent root resolution design.

## 7. References

- ITU-T X.660 / ISO/IEC 9834-1 — *Procedures for the operation of OSI
  Registration Authorities: general procedures and top arcs of the
  international object identifier tree*
- ITU-T X.680 / ISO/IEC 8824-1 — *Abstract Syntax Notation One (ASN.1)*
  (defines OBJECT IDENTIFIER and OID-IRI)
- IETF RFC 3061 — *A URN Namespace of Object Identifiers* (`urn:oid:`)
- W3C. *Decentralized Identifiers (DIDs) v1.0*. W3C Recommendation,
  19 July 2022 (DID data model, `alsoKnownAs`, resolution)
- EN 18219:2026 — Digital product passport — Unique identifiers
