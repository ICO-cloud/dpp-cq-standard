# Personal Information Impact Assessment (PIA / DPIA) — Summary

**ICO Std 2001 DPP-CQ — Privacy Impact Assessment, public summary**
**Version:** v1.0 (aligned to standard v2.0.0-draft) · **Date:** 2026-08

> This is the public summary of the Personal Information Impact Assessment for
> the DPP-CQ specification and reference resolver services. It follows the
> accountability logic of GDPR Art. 35 (DPIA), the governance direction of
> ISO/IEC 42001:2023, and — for deployments within China — the requirements
> of China's Personal Information Protection Law (PIPL). National-standard
> mappings are informative deployment support, not normative references of the
> standard. It is a living document; the full assessment is maintained
> internally by the ICO Technical Secretariat and shared with adopting
> institutions and regulators on request.

---

## 1. Data flows in scope

| Flow | Personal data involved? | Description |
|---|---|---|
| Consumer scan → verification page | No (or minimal: server logs) | Public product/credential data; no account required |
| Credential issuance | Possibly (artisan / assessor names) | Issuer records product and, with consent, named artisan or assessor details |
| Business verification (deep) | Possibly | Authorized verifiers receive selectively disclosed claims |
| Root resolver operation | Minimal | Resolution metadata, status list queries, security logs |

## 2. Privacy risks and mitigation

| Risk | Severity | Mitigation |
|---|---|---|
| Personal data (artisan names) over-exposed via public credentials | Medium | Personal claims placed in selective-disclosure class; public payloads minimized; consent recorded by issuer |
| Cross-border transfer of personal data | Medium | Default mode is **hash-only cross-border**: raw data stays in the issuing jurisdiction; only irreversible hash fingerprints anchor internationally |
| Credential correlation / tracking of consumers | Medium | BBS+ unlinkable presentations recommended for repeat verification; no consumer accounts for basic scanning; status list query privacy via BitstringStatusList |
| Over-collection by issuers | Medium | Schema marks optional fields; data minimization principle in spec; disclosure-class table in credential-formats annex |
| Retention beyond necessity | Low-Medium | `dataLifecycle.retentionPolicy` and `deletionPolicy` fields expected on v2.0 credentials (public minimum; full policy maintained by the issuer); default 5-year post-expiry for raw assessment data |
| Security breach of resolver | Medium (impact) | STRIDE threat model; five-layer defense-in-depth; API key hashing (SHA-256, timing-safe compare); security.txt / vulnerability disclosure policy |
| AI assessment data profiling | Low | AI only pre-scores; human assessor makes the final decision; AI usage disclosed per credential |

## 3. Data subject rights

- **Consent:** artisan / assessor personal data is included only with consent;
  consent withdrawal triggers credential update or revocation.
- **Access & correction:** data subjects contact the issuing body (the data
  controller identified in `dataLifecycle.dataController`); root resolver
  redirects requests to the controller.
- **Erasure:** on revocation or expiry-plus-retention, raw data is deleted or
  anonymized; hash anchors and status records are retained for evidentiary
  integrity and contain no reconstructable personal data.
- **No marketing use:** verification services must not use scan data for
  advertising profiling; this is an adoption condition in the issuer agreement.

## 4. Cross-border legal basis

- China (PIPL): hash-only mode means no raw personal information leaves the
  jurisdiction; where full transfer is needed, issuers apply the statutory
  route (standard contract / security assessment / certification as applicable).
- EU (GDPR): transfers outside the EEA rely on SCCs or adequacy where
  applicable; the default architecture avoids transferring personal data at all.

## 5. Residual risks & follow-ups

1. Formal third-party privacy audit of the reference resolver (P1).
2. Full GDPR/PIPL dual-compliance white paper with template data-processing
   agreements (P1).
3. Privacy-preserving status list checks (private information retrieval)
   evaluation (P2).

---

*Contact for privacy matters: info@icoun.org · Full assessment available to
adopting institutions and competent authorities.*
