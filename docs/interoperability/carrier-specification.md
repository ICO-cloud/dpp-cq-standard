# Data Carrier Specification
## Normative Annex — ICO Std 2001 v2.0

> **Status**: Normative · Part of ICO Std 2001:2026 (DPP-CQ v2.0)
> **Maintained at**: `docs/interoperability/carrier-specification.md`
> **Version**: 2.0.0-draft

---

## 1. Scope

This annex specifies the three-tier physical carrier system for DPP-CQ
credentials. It defines carrier levels, security profiles, reader requirements,
and the principles governing carrier selection. Aligned with white paper §7.7.

## 2. Three-Tier Carrier Model

| Level | Carrier | Security Profile | Reader Requirement | Clone Resistance |
|---|---|---|---|---|
| **L1** | Open QR Code (GS1 Digital Link in interop profile) | Cloneable; authenticity via registry verification | Any smartphone camera | None (registry-dependent) |
| **L2** | SDM Secure NFC (NTAG 424 DNA class) | Per-scan cryptographic SUN authentication | Any NFC-capable phone, NDEF open read | High (hardware-enforced) |
| **L3** | Tamper-Evident NFC (TagTamper class) | Tamper detection + SDM + physical evidence | Any NFC-capable phone | Very High (tamper-evident) |

## 3. Level Definitions

### 3.1 L1 — Open QR Code

**Definition**: A printed QR code encoding a GS1 Digital Link URI that resolves
to the DPP-CQ credential.

**Requirements:**
- **Encoding**: GS1 Digital Link URI per `docs/interoperability/gs1-digital-link-mapping.md`
- **Size**: Minimum 25mm × 25mm for reliable scanning; recommended 30mm × 30mm
- **Error correction**: Level M (15%) minimum; Level H (30%) recommended for
  harsh environments
- **Quiet zone**: Minimum 4 modules on all sides
- **Print quality**: ISO/IEC 15415 Grade C (2.0) minimum; Grade B recommended

**Security model**: The QR code is inherently cloneable. Authenticity is
established by resolving the URI and verifying the credential's cryptographic
signature against the issuer's DID document. No security through obscurity.

**Use cases**:
- Mass-market products where cost is a primary constraint
- Products where NFC is impractical (flexible packaging, small items)
- Consumer-facing verification (any smartphone can scan)

### 3.2 L2 — SDM Secure NFC

**Definition**: An NFC tag (NTAG 424 DNA or equivalent) with Secure Direct
Message (SDM) capability, providing per-scan cryptographic authentication.

**Requirements:**
- **Chip class**: NXP NTAG 424 DNA (or equivalent with ISO 18092 compliance)
- **UID**: Unique, factory-set 7-byte UID (read-only)
- **SDM**: Secure Direct Message with AES-128 encryption
  - SUN (Secure Unique NFC) message generated per scan
  - Includes tag UID, scan counter, and AES-CMAC authentication
- **Memory**: Minimum 1024 bytes user memory for credential metadata
- **NDEF format**: NDEF message **MUST** contain the GS1 Digital Link URI as
  the primary payload; **SHOULD** also include an SDM mirror URL for
  authentication

**Security model**: Each NFC tap generates a unique cryptographic response
(SUN message) that proves the tag is genuine and has not been cloned. The
verification backend validates the AES-CMAC against the tag's secret key.

**Use cases**:
- Premium products requiring anti-counterfeiting (wine, spirits, luxury goods)
- Products sold in environments where QR scanning is inconvenient
- Dual-carrier configurations (see §5)

### 3.3 L3 — Tamper-Evident NFC

**Definition**: An NFC tag with integrated tamper-detection capability,
providing both cryptographic authentication and physical evidence of
tampering.

**Requirements:**
- **Chip class**: NTAG 424 DNA with TagTamper feature, or equivalent
  (e.g., NXP NTAG 424 DNA TT)
- **Tamper detection**: Conductive trace that breaks upon removal;
  generates a tamper-evident flag in the SDM response
- **Tamper response**: SDM response **MUST** include tamper status bit;
  verification page **MUST** display warning if tamper flag is set
- **Adhesive**: Tamper-evident destructible label material; removal causes
  irreversible physical damage

**Security model**: Combines L2's cryptographic authentication with physical
tamper evidence. If the tag is removed from its original surface, the
conductive trace breaks, and subsequent scans report tampered status.

**Use cases**:
- High-value products (precious metals, luxury watches, rare teas)
- Regulated products requiring chain-of-custody evidence
- Products where label swapping is a known risk

## 4. Open Carrier Principle

Aligned with EU ESPR Art. 9 and EN 18220, DPP-CQ mandates the **open carrier
principle**:

> Every product **MUST** be readable with generally available means — no
> proprietary app, registration, or fee. Security is achieved through
> cryptographic verification of the resolved data, never through hiding
> the payload.

### 4.1 Requirements

1. **No proprietary apps**: The QR code or NFC tag **MUST** be readable with
   the device's native camera or NFC reader. No specialized app required.
2. **No registration wall**: Accessing the verification page **MUST NOT**
   require user registration or account creation.
3. **No fee**: Accessing basic verification (authenticity + core credential
   data) **MUST** be free of charge.
4. **Open standards**: All data formats **MUST** be based on open standards
   (W3C VC, GS1 Digital Link, NDEF).

### 4.2 Verification Page

The verification page (resolved via the Digital Link URI) **MUST**:
- Display product name, quality grade, and issuer information
- Show credential validity status (valid / revoked / expired)
- Indicate which carrier was presented (QR / NFC / Tamper-evident)
- Provide links to full credential data and conformity claims
- Be accessible without JavaScript (basic functionality via server-rendered HTML)

## 5. Dual Carrier Rule

For products in the GS1 interop profile, the **dual carrier rule** applies:

> Products **SHOULD** carry both an L1 open QR code (universal scanning,
> retail/customer flows) and an L2 SDM NFC tag (cryptographic authenticity);
> both **MUST** resolve to the same passport, and the verification page
> **MUST** indicate which carrier was presented.

### 5.1 Configuration

| Configuration | When to Use |
|---|---|
| L1 only | Cost-constrained; low-counterfeit-risk products |
| L1 + L2 | Standard for GS1 interop profile; most consumer products |
| L2 only | Products where QR is impractical; NFC-only packaging |
| L3 only | High-value; tamper-evident required |
| L1 + L2 + L3 | Premium tier; QR for retail, NFC for authentication, tamper evidence for chain-of-custody |

### 5.2 Carrier Registration

The carrier tier configuration **MUST** be recorded in the credential:

```json
{
  "carrierTier": {
    "level": "L2",
    "primary": "sdm-nfc",
    "secondary": "open-qr",
    "nfcChipType": "NTAG-424-DNA",
    "tamperEvident": false,
    "dualCarrier": true
  }
}
```

## 6. Resolver Behavior

The ICO resolver **MUST** handle carrier-specific behavior:

| Carrier | Resolution | Authentication |
|---|---|---|
| L1 (QR) | Resolve Digital Link URI → fetch credential → verify signature | Credential-level only |
| L2 (SDM NFC) | Parse SUN message → validate AES-CMAC → fetch credential → verify signature | Tag-level + credential-level |
| L3 (Tamper NFC) | Parse SUN message → check tamper flag → validate AES-CMAC → fetch credential → verify signature | Tamper check + tag-level + credential-level |

### 6.1 Response Codes

| Scenario | Response |
|---|---|
| Valid credential, genuine tag | `200 OK` — full verification result |
| Valid credential, tamper flag set (L3) | `200 OK` — verification result + tamper warning |
| Revoked credential | `200 OK` — status: revoked, with details |
| Invalid SUN message (L2/L3) | `401 Unauthorized` — tag authentication failed |
| Unknown DID | `404 Not Found` |

---

*Part of ICO Std 2001:2026 (DPP-CQ v2.0.0-draft) · © 2026 International Communication Organization (ICO)*
*Licensed under CC BY 4.0*
