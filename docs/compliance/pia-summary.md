# Privacy Impact Assessment (PIA) Summary
## Public Document — ICO Std 2001 v2.0

> **Status**: Public · Part of ICO Std 2001:2026 (DPP-CQ v2.0)
> **Maintained at**: `docs/compliance/pia-summary.md`
> **Version**: 2.0.0-draft
> **Last updated**: September 2026

---

## 1. Purpose

This document provides a public summary of the Privacy Impact Assessment (PIA)
conducted for the DPP-CQ v2.0 standard framework. It is maintained as a
normative reference per white paper §8.3.

This PIA summary addresses requirements under both the EU GDPR (Art. 35) and
China's PIPL (Art. 55).

## 2. Data Flow Architecture

DPP-CQ employs a **"data localization, hash cross-border"** architecture:

```
┌─────────────────────────────────────────────────────────┐
│                    DATA FLOW MODEL                       │
│                                                         │
│  ┌──────────┐     ┌──────────────┐     ┌──────────┐   │
│  │ Issuer   │────▶│ Local Store  │────▶│ Hash     │   │
│  │ (raw data│     │ (jurisdiction│     │ Anchor   │   │
│  │  created)│     │  of origin)  │     │ (global) │   │
│  └──────────┘     └──────────────┘     └──────────┘   │
│        │                                    │          │
│        ▼                                    ▼          │
│  ┌──────────┐                        ┌──────────┐     │
│  │ Selective│                        │ Verifier │     │
│  │ Disclosure│◀──────────────────────│ (receives│     │
│  │ (BBS+/SD │                        │  only    │     │
│  │  -JWT)   │                        │  claims) │     │
│  └──────────┘                        └──────────┘     │
└─────────────────────────────────────────────────────────┘
```

### 2.1 Data Categories

| Category | Examples | Storage | Cross-Border |
|---|---|---|---|
| **Product identity** | Name, category, grade, GI number | Local + Hash anchor | Hash only |
| **Origin data** | Region, country, coordinates | Local | Hash only |
| **Cultural data** | Heritage status, craft method | Local | Hash only |
| **Artisan personal data** | Name, title, biography | Local (restricted) | Never |
| **Supply chain data** | Batch numbers, locations, entities | Local | Hash only |
| **Quality attributes** | Lab results, specifications | Local | Hash only |
| **Sustainability data** | PCF, material composition | Local | Hash only |
| **Assessment data** | AI disclosure, methodology refs | Local | Hash only |
| **Lifecycle metadata** | Controller, retention, privacy URI | Embedded in credential | Yes (public) |

### 2.2 Cross-Border Data Transfer

| Data Type | Transfer Method | Legal Basis |
|---|---|---|
| Hash fingerprints | Blockchain / distributed ledger | Hash = no identifiable information; not personal data |
| Credential metadata (public claims) | Verifiable Credential over HTTPS | Consent / legitimate interest |
| Selective disclosures | BBS+ / SD-JWT presentation | Consent (per disclosure) |
| Personal data (artisan info) | Never transferred cross-border | N/A (localized) |

## 3. Risk Assessment

### 3.1 Risk Register

| ID | Risk | Likelihood | Impact | Mitigation | Residual Risk |
|---|---|---|---|---|---|
| R-01 | Credential data leakage via resolver | Low | High | Hash-only cross-border; selective disclosure; encrypted storage | Low |
| R-02 | Artisan personal data exposure | Medium | High | Restricted (R) disclosure class; localized storage; consent required | Low |
| R-03 | Supply chain data competitive exposure | Medium | Medium | Holder-selectable disclosure; R-class for batch data | Low |
| R-04 | QR code cloning (L1) | High | Low | Clone = same data; authenticity via cryptographic verification, not QR secrecy | Accepted |
| R-05 | NFC tag spoofing (L2) | Low | High | SDM per-scan cryptographic authentication; AES-CMAC validation | Low |
| R-06 | Cross-border data sovereignty violation | Low | Critical | "Data localization, hash cross-border" architecture; configurable jurisdiction | Low |
| R-07 | Credential over-disclosure | Medium | Medium | Disclosure classification (P/H/R); holder controls presentation scope | Low |
| R-08 | Retention policy violation | Low | Medium | `dataLifecycle` metadata; automated deletion triggers | Low |

### 3.2 Risk Acceptance

All risks are assessed as **Low residual risk** after mitigation, except R-04
(QR cloning) which is an accepted risk by design — the security model does not
rely on QR code secrecy.

## 4. Data Subject Rights

DPP-CQ supports the following data subject rights:

| Right | GDPR Art. | PIPL Art. | DPP-CQ Implementation |
|---|---|---|---|
| **Right to information** | 13-14 | 17 | `dataLifecycle.privacyNoticeUri` in every credential |
| **Right of access** | 15 | 45 | Holder can retrieve full credential via DID resolution |
| **Right to rectification** | 16 | 46 | Issuer can issue updated credential; old version superseded |
| **Right to erasure** | 17 | 47 | Issuer can revoke credential; local data deletion per `dataLifecycle.deletionRules` |
| **Right to restrict processing** | 18 | — | Selective disclosure limits data exposure |
| **Right to data portability** | 20 | 45 | Standard VC format enables portability |
| **Right to object** | 21 | 44 | Holder controls which claims to disclose |
| **Right to withdraw consent** | 7(3) | 15 | Revocation mechanism; artisan can withdraw consent for personal data disclosure |

## 5. Cross-Border Legal Basis

### 5.1 EU GDPR

| Transfer Mechanism | Applicability |
|---|---|
| Hash = non-personal data | Primary basis for hash cross-border |
| Standard Contractual Clauses (SCCs) | For any residual personal data transfers |
| Consent | For selective disclosure presentations |
| Legitimate interest | For public claims in verification flows |

### 5.2 China PIPL

| Transfer Mechanism | Applicability |
|---|---|
| Data localization | Raw data stored within China; only hashes cross borders |
| CAC security assessment | Not required (no personal data crosses border) |
| Standard contract | For any future cross-border personal data needs |
| Certification | ICO standard framework certification available |

### 5.3 Other Jurisdictions

| Jurisdiction | Approach |
|---|---|
| Southeast Asia | Flexible regional node deployment; configurable data storage |
| Middle East / GCC | Regional node deployment; no mandatory cross-border transfer |
| Global South | Lightweight solutions; data stays local |

## 6. Data Lifecycle Metadata

Every DPP-CQ v2.0 credential carries a `dataLifecycle` record:

```json
{
  "dataLifecycle": {
    "controller": "did:ico:issuer:zjtea-assoc",
    "controllerContact": "privacy@zjtea-assoc.example",
    "retentionPolicy": {
      "retentionPeriod": "P5Y",
      "basis": "contractual-obligation",
      "deletionTrigger": "expiration"
    },
    "storageJurisdiction": "CN",
    "crossBorderMode": "hash-only",
    "deletionRules": {
      "personalData": "deleted-within-30-days-of-withdrawal",
      "credentialData": "retained-for-verification-history",
      "hashAnchors": "permanent"
    },
    "privacyNoticeUri": "https://zjtea-assoc.example/privacy",
    "piaSummaryUri": "https://resolver.icoun.org/pia/zjtea-assoc"
  }
}
```

## 7. Governance

- This PIA summary is reviewed **annually** or upon significant standard changes
- The ICO Technical Committee maintains this document
- Stakeholder feedback is accepted via info@icoun.org
- Material changes require public review period (minimum 30 days)

---

*Part of ICO Std 2001:2026 (DPP-CQ v2.0.0-draft) · © 2026 International Communication Organization (ICO)*
*Licensed under CC BY 4.0*
