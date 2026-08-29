# Data Carrier Specification — Three-Tier Physical Carriers

**ICO Std 2001 — Carrier Annex (Normative)**
**Version:** v2.0.0-draft · **Status:** Public Review Draft · **Date:** 2026-08

> Defines the physical data carrier requirements for DPP-CQ products.
> Aligned with EN 18220:2026 (data carrier for product data), ISO/IEC 18004
> (QR code), ISO/IEC 15415 (2D print quality), ISO/IEC 14443 (NFC) and the
> NFC Forum NDEF specification.

---

## 1. Open Carrier Principle

Consistent with EU DPP requirements (ESPR Art. 9; EN 18220), the data carrier
on a product **MUST** be readable with **generally available means** — a
standard smartphone camera or NFC reader, without any proprietary application,
registration, or fee. The carrier resolves to the product passport where the
consumer can choose the depth of verification.

## 2. Carrier Levels

DPP-CQ defines three carrier levels. Products **MUST** carry at least L1;
higher-value or higher-counterfeit-risk products **SHOULD** carry L2; flagship
/ high-value cultural goods **MAY** carry L3.

| Level | Carrier | Standard | Security | Cost | Reader requirement |
|---|---|---|---|---|---|
| **L1** | Open QR code | ISO/IEC 18004; GS1 Digital Link 1.6 | Low (cloneable); authenticity established via registry lookup | Very low | Any camera |
| **L2** | Secure NFC with SDM | ISO/IEC 14443 Type 4; NXP NTAG 424 DNA class | Medium-high (Secure Dynamic Messaging, per-scan SUN authentication) | Medium | Any NFC phone; NDEF open read |
| **L3** | Tamper-evident secure NFC | NTAG 424 DNA TagTamper class | High (tamper detection + SDM + on-tag status) | Higher | Any NFC phone |

### 2.1 L1 — Open QR (mandatory minimum)

- QR **MUST** encode an HTTPS URI; in the GS1 interop profile this **MUST** be
  a GS1 Digital Link URI (see `gs1-digital-link-mapping.md`).
- Print quality **SHOULD** reach grade **B or better** per ISO/IEC 15415
  measured under the intended production conditions.
- QR **MUST NOT** be the sole anti-counterfeiting feature for goods above the
  platform's defined high-risk threshold; L2 or equivalent is required then.
- QR size and quiet zone **MUST** follow ISO/IEC 18004 minimum modules for the
  expected scanning distance (consumer packaging: ≥ 10mm nominal recommended).

### 2.2 L2 — SDM Secure NFC

- Chip **MUST** implement Secure Dynamic Messaging (SDM), with per-read
  cryptographic SUN message verification at the resolver (NTAG 424 DNA class).
- The NDEF record **MUST** remain openly readable (open carrier principle);
  security comes from SDM authentication, not from hiding the payload.
- The tag UID **MUST** be registered in the issuer's credential record
  (`authenticityMarks.identifier`) and bound to the product DID at issuance.
- Resolver **MUST** reject scans whose SDM message fails authentication or
  whose UID is not registered (returns "unregistered carrier" — a designed
  anti-counterfeit signal, not an error).

### 2.3 L3 — Tamper-evident NFC

- L3 chips detect package opening (TagTamper status). The tamper state **MUST**
  be surfaced in the verification UI ("package seal status").
- A triggered tamper flag does not automatically revoke the credential but
  **MUST** be displayed prominently and logged.

## 3. Dual-Carrier Rule

Products in the GS1 interop profile **SHOULD** carry **both L1 and L2** on the
same packaging unit:

- The **QR** guarantees universal open readability and retail/customer scanning.
- The **NFC** provides per-scan cryptographic authenticity.
- Both resolve to the **same** passport URI / credential, and the verification
  page **MUST** indicate which carrier was presented.

## 4. Resolver Behavior

1. Scan opens the passport URI (Digital Link or `did:ico` resolver redirect).
2. Resolver identifies carrier type from query parameters / NDEF metadata.
3. For NFC SDM scans, resolver verifies the SUN message before rendering
   "authentic carrier"; failed verification renders a clear warning.
4. The consumer-facing page **MUST** show, without login: product identity,
   quality grade summary, issuer, and a privacy notice link.
5. Selective disclosure (SD-JWT / BBS+) governs deeper data; verifiers in a
   business relationship obtain disclosed claims via the credential exchange.

## 5. References

- EN 18220:2026 — Data carrier for product data (CEN-CENELEC JTC 24)
- ISO/IEC 18004:2015 — QR code bar code symbology
- ISO/IEC 15415:2011 — 2D print quality testing
- ISO/IEC 14443 — Contactless integrated circuit cards (Type 4)
- NFC Forum, NDEF specification
- NXP NTAG 424 DNA / TagTamper functional specifications (implementer reference)
- Regulation (EU) 2024/1781 (ESPR), Art. 9
