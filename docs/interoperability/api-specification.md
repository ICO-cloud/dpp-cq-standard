# Open Interoperability API — Passport Lifecycle & Searchability

**ICO Std 2001 — API Annex (Normative)**
**Version:** v2.0.0-draft · **Status:** Public Review Draft · **Date:** 2026-09

> Defines the open, machine-to-machine API surface for DPP-CQ passports across
> their lifecycle. Aligned with **EN 18222:2026** *Digital product passport —
> Application Programming Interfaces (APIs) for the product passport lifecycle
> management and searchability* (CEN/CENELEC JTC 24), and expressed as a
> RESTful API (OpenAPI 3.0). This annex is the normative API contract; the
> Root Resolver endpoints in White Paper Annex A.3 are the discovery and
> status subset of this surface.

---

## 1. Scope and Design Principles

DPP-CQ defines one open API surface used by every compliant node, issuer
resolver, and business-system integration. The design follows EN 18222:

1. **REST, stateless** — resources addressed by stable HTTPS URIs; standard
   HTTP methods (`GET`, `POST`, `PUT`/`PATCH`, `DELETE`); no server-side
   session affinity (EN 18222 REST API definition).
2. **Searchability** — a DPP **MUST** be locable from any of its registered
   identifiers (product DID, GTIN, batch/lot, and — where bound — OID) without
   prior bilateral arrangement between systems.
3. **Lifecycle completeness** — create, read, update/version, archive, and
   deactivate/revoke are all exposed through the API; passport data **MUST**
   remain retrievable even if the original economic operator ceases activity
   (mirrors EN 18221 persistence intent; API surface defined here).
4. **Gateway resolution** — a read request **MUST** be redirected/routed to
   the authoritative data holder for the product, including across hybrid and
   cross-border deployments.
5. **Open access for public data; authorization for the rest** — public
   passport data is readable without registration or fee; business-sensitive
   and personal claims are released only through credential exchange with
   selective disclosure (see `credential-formats.md`).

## 2. Conformance Levels

| Level | Meaning | Requirements |
|---|---|---|
| **DPP-CQ Read** | Resolvers, consumer verification pages | Sections 4.1–4.3, 6, 7 |
| **DPP-CQ Lifecycle** | Issuers, node operators | All sections |
| **DPP-CQ Search** | Registry/gateway services | Read level plus §4.4 |

All conformance levels **MUST** publish an OpenAPI 3.0 description at
`/.well-known/dppcq-api/openapi.json` and a human-readable status/terms page.

## 3. Resource Model

| Resource | Canonical path | Description |
|---|---|---|
| Passport | `/passports/{did}` | The DPP-CQ passport (credential record) for one product/batch |
| Credential | `/credentials/{credentialId}` | A signed verifiable credential |
| Identifier alias | `/identifiers/{scheme}/{value}` | Lookup by `gtin`, `oid`, batch, or other registered identifier |
| Status | `/credentials/{credentialId}/status` | Valid / suspended / revoked / expired |
| Proof anchor | `/proofs/{hash}` | Hash anchoring and timestamp attestation record |
| Event stream | `/passports/{did}/events` | Supply-chain / lifecycle events (EPCIS-compatible, P1) |
| Versions | `/passports/{did}/versions` | Version history and archival copies |

## 4. Methods

### 4.1 Read (public)

- `GET /passports/{did}` returns the public passport record.
- Content negotiation: clients **MAY** request `application/json`,
  `application/ld+json`, or `application/pdf` (human-readable summary);
  servers **MUST** support at least JSON and JSON-LD.
- A public response **MUST NOT** require an account, API key, or payment for
  the open data classes (product identity, quality grade summary, issuer,
  privacy notice — see `carrier-specification.md` §4).
- Responses carry standard caching headers and a `Link` header referencing the
  JSON-LD context and the machine-readable conformity claim.

### 4.2 Search / resolve by identifier

- `GET /identifiers/gtin/{gtin}`, `GET /identifiers/oid/{oid}`,
  `GET /identifiers/batch/{batch}` → `307`/`308` redirect or canonical object
  pointing to the authoritative passport URI.
- Resolution is identifier-scheme agnostic: GTIN (GS1), DID (W3C), and OID
  (ISO/ITU-T, see `identifier-mapping.md`) all resolve to the same passport
  when bound.
- Search responses are **MUST** be deterministic for a given identifier;
  ambiguous matches return a list object, never an arbitrary single record.

### 4.3 Status and verify

| Method & path | Function |
|---|---|
| `GET /credentials/{id}/status` | Status per W3C BitstringStatusList |
| `POST /credentials/verify` | Verify signature, status, validity window |
| `GET /proofs/{hash}` | Retrieve hash-anchor / timestamp attestation |

Status changes (suspend/revoke) **MUST** propagate across QR and NFC
resolution paths within the operator's stated SLA (target < 5 minutes).

### 4.4 Lifecycle operations (authorized)

| Method & path | Function |
|---|---|
| `POST /passports` | Create / register a new passport |
| `PUT`/`PATCH /passports/{did}` | Update mutable fields; immutable claims are versioned, not overwritten |
| `GET /passports/{did}/versions` | List and retrieve archived versions |
| `POST /credentials/{id}/revoke` | Revoke / deactivate |
| `POST /passports/{did}/transfer` | Transfer custodianship to a backup operator (continuity) |

Lifecycle calls **MUST** be authenticated (OAuth 2.0 / OIDC bearer tokens or
W3C VC-based authorization), authorized per role, and fully audited. Every
state change **MUST** produce a new hash anchor.

## 5. Access Control, Confidentiality

- Public read tier: no credentials.
- Business tier: OAuth 2.0 scopes mapped to claim classes; confidential
  business data is exchanged via SD-JWT / BBS+ selective disclosure rather
  than bulk export.
- Personal tier: released only with lawful basis / data-subject consent.
- The API **MUST NOT** expose undisclosed claim values through enumeration,
  search indexing, or error messages.
- Security/confidentiality requirements will additionally track prEN 18239
  (access rights, system security, business confidentiality) once published.

## 6. Error Handling

Standard HTTP status codes; errors use RFC 7807 `application/problem+json`
with a stable `type`, `title`, `detail`, and a DPP-CQ `code`. An unknown or
unregistered carrier/identifier **MUST** return the designated
`unregistered-identifier` response — an intentional anti-counterfeit signal,
not a server error.

## 7. Non-functional Requirements

- HTTPS (TLS 1.2+) mandatory for all endpoints.
- Rate limits and machine-readable service description **MUST** be published;
  public read endpoints **SHOULD** remain usable by standard consumer
  verification clients without a key.
- Versioning via URI major version (`/v1/…`) plus an `OpenAPI` document;
  breaking changes require a new major version and a ≥ 12-month overlap
  window (White Paper §7.6).
- Regional deployments **MAY** implement the full surface locally; only the
  read/status/proof methods required for cross-border verification are
  expected at every node.

## 8. Relationship to Root Resolver API (Annex A.3)

The six Root Resolver endpoints in White Paper Annex A.3
(`/v1/did/{did}`, `/v1/credential/{id}/status`, `/v1/credential/verify`,
`/v1/register`, `/v1/revoke`, `/v1/proof/{hash}`) are the discovery, status,
and anchoring subset of this annex. Deployments exposing only that subset
conform at **DPP-CQ Read** level; issuer and node systems **MUST** implement
the lifecycle and search methods of §4 to claim **DPP-CQ Lifecycle/Search**
conformance.

## 9. References

- EN 18222:2026 — Digital product passport — APIs for product passport
  lifecycle management and searchability (CEN/CENELEC JTC 24)
- EN 18216:2026 — Data exchange protocols
- EN 18221:2026 — Data storage, archiving and persistence
- prEN 18239 — Access rights management, information system security and
  business confidentiality (under development)
- OpenAPI Specification 3.0/3.1 — OpenAPI Initiative
- IETF RFC 7807 — Problem Details for HTTP APIs
- W3C Verifiable Credentials Data Model v2.0; BitstringStatusList
- GS1 EPCIS 2.0 — event model for the P1 event stream
