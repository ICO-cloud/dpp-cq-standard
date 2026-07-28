---
layout: page
title: "Credential Examples"
permalink: /examples.html
---

# DPP-CQ Credential Examples

> Sample verifiable credentials conforming to the DPP-CQ JSON Schema (ICO Std 2001-2026).

---

## Example 1: West Lake Longjing Tea

A geographical indication tea product with intangible cultural heritage data, full traceability, and dual physical carriers (NFC + QR).

```json
{
  "@context": [
    "https://www.w3.org/ns/credentials/v2",
    "https://icoun.org/contexts/dpp-cq/v1"
  ],
  "id": "did:ico:dpp:tea:longjing-xh-2026-001",
  "type": [
    "VerifiableCredential",
    "DPPQualityCredential",
    "CulturalHeritageCredential"
  ],
  "issuer": "did:ico:issuer:zjtea-assoc",
  "issuanceDate": "2026-07-15T00:00:00Z",
  "expirationDate": "2027-07-14T23:59:59Z",
  "credentialStatus": {
    "id": "https://resolver.icoun.org/v1/status/001#42",
    "type": "BitstringStatusListEntry",
    "statusPurpose": "revocation",
    "statusListIndex": "42",
    "statusListCredential": "https://resolver.icoun.org/v1/status/001"
  },
  "credentialSubject": {
    "id": "did:ico:dpp:tea:longjing-xh-2026-001",
    "productName": {
      "zh": "西湖龙井茶",
      "en": "West Lake Longjing Tea"
    },
    "category": "geographical-indication-tea",
    "qualityGrade": "Premium Grade 1",
    "origin": {
      "type": "GeographicalIndication",
      "giNumber": "GI-CN-0001",
      "region": "West Lake Production Area, Hangzhou",
      "country": "CN"
    },
    "culturalData": {
      "heritageStatus": "National Intangible Cultural Heritage",
      "heritageYear": 2008,
      "heritageNumber": "Ⅷ-148",
      "craftMethod": "Hand-fired with ten traditional techniques",
      "craftHistory": "Longjing tea has a history of over 1,200 years.",
      "culturalNarrative": "One of China's Ten Famous Teas, known for green color, fragrant aroma, sweet taste, and beautiful shape."
    },
    "traceability": {
      "harvestDate": "2026-03-28",
      "processLocation": "Longwu Tea Town, Hangzhou",
      "batchNumber": "XH20260328A01"
    },
    "qualityAttributes": {
      "appearance": "Flat and smooth, tender green color",
      "aroma": "Long-lasting tender chestnut aroma",
      "taste": "Fresh, mellow, and sweet aftertaste"
    },
    "authenticityMarks": [
      {
        "type": "nfc-chip",
        "identifier": "NTAG-424-DNA-001",
        "description": "NFC chip with unique ID, tamper-evident"
      },
      {
        "type": "qr-code",
        "identifier": "did:ico:dpp:tea:longjing-xh-2026-001"
      }
    ]
  },
  "proof": {
    "type": "BbsBlsSignature2020",
    "created": "2026-07-15T10:30:00Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:ico:issuer:zjtea-assoc#keys-1",
    "proofValue": "t8MwnQJvN9..."
  }
}
```

### Key Highlights

| Module | Data Included |
|--------|---------------|
| **Base Identity** | DID-based unique identifier |
| **Quality Data** | Premium Grade 1, sensory attributes, lab test specs |
| **Cultural Data** | National ICH status, traditional craft method, 1,200-year history |
| **Geographical Indication** | GI-CN-0001, West Lake production area |
| **Traceability** | 4-step supply chain from harvest to packaging |
| **Credential Proof** | BBS+ signature for selective disclosure support |

### Physical Carriers

- **NFC:** NTAG 424 DNA chip — secure, tamper-evident, supports cryptographic verification
- **QR Code:** Encodes the credential DID for instant lookup via [verify.oppscc.org.cn](https://verify.oppscc.org.cn)

---

## Full Example File

The complete example file with all fields (including supply chain steps, specifications, certifications) is available at:

📄 [longjing-tea.json](https://github.com/ICO-cloud/dpp-cq-standard/blob/main/examples/longjing-tea.json)

---

## Category Coverage

The DPP-CQ schema supports the following product categories:

| Category | Code | Example Use Case |
|----------|------|-----------------|
| GI Tea | `geographical-indication-tea` | Longjing, Da Hong Pao, Pu'er |
| ICH Ceramic | `intangible-cultural-heritage-ceramic` | Jingdezhen porcelain, Yixing pottery |
| Haute Couture | `haute-couture-apparel` | Handcrafted Chinese haute couture |
| GI Food | `geographical-indication-food` | Regional specialty foods |
| Handicraft | `handicraft` | Embroidery, lacquerware, woodwork |
| Specialty Agricultural | `specialty-agricultural-product` | Regional herbs, honey, oils |
| Cultural Creative | `cultural-creative-product` | Museum collaborations, cultural IP |
| Other | `other` | Additional categories |
