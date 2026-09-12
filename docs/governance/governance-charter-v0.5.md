# ICO Standards Governance Charter

**Version 0.5 — Working Draft**
**Date:** September 2026
**Status:** Open for Public Comment (Sep 1 – Oct 15, 2026)
**Author:** ICO Technical Secretariat

---

## 1. Purpose

This Charter establishes the governance framework for the **ICO Digital Trust Standards Framework** — the open, multi-stakeholder standards development process administered by the International Communication Organization (ICO).

The Charter defines:
- How standards are proposed, developed, reviewed, and approved
- Who participates and how decisions are made
- How conflicts are resolved and how the governance framework itself evolves

This is **Version 0.5** — an interim governance framework sufficient to support the public review and stabilization of DPP-CQ v2.0. It will be refined into v1.0 based on community feedback and the outcomes of initial working group operations.

---

## 2. Principles

The ICO Standards development process is guided by the following principles:

| Principle | Meaning |
|---|---|
| **Openness** | Any qualified stakeholder may participate; no unreasonable barriers to entry |
| **Transparency** | All proceedings, drafts, and decisions are publicly documented |
| **Consensus** | Decisions seek broad agreement; dissent is recorded and addressed |
| **Due Process** | Adequate notice, comment periods, and appeal mechanisms are maintained |
| **Balance** | No single interest group dominates; multiple perspectives are sought |
| **Neutrality** | Standards are technology-neutral where possible; no vendor lock-in |
| **Inclusivity** | Developing economies and small organizations have meaningful participation pathways |

---

## 3. Governance Structure

```
┌─────────────────────────────────────────────┐
│              ICO Standards Council           │
│  Final approval authority · Strategic direction  │
│  Composition: Founder + appointed members    │
├─────────────────────────────────────────────┤
│           Technical Secretariat              │
│  Day-to-day standards administration         │
│  Editor coordination · Document management   │
├─────────────────────────────────────────────┤
│              Working Groups                  │
│  Technical content development               │
│  Community review · Consensus building       │
├─────────────────────────────────────────────┤
│          Community Contributors              │
│  Issue reports · Public comments · Reviews   │
└─────────────────────────────────────────────┘
```

### 3.1 ICO Standards Council

**Role:** The final approval authority for ICO standards. The Council:
- Approves standards for publication (Public Review → Final Standard)
- Resolves appeals and disputes that cannot be settled within Working Groups
- Sets strategic direction for the standards portfolio
- Approves amendments to this Charter

**Composition (v0.5):**
- **Chair:** ICO Executive Chairman (founder)
- **Members:** To be appointed based on stakeholder representation needs (target: 5–9 members from industry, academia, civil society, and government advisory roles)
- **Secretary:** Technical Secretariat lead (non-voting, administrative)

**Decision Rules (v0.5):**
- Quorum: 50% of voting members
- Approval: Simple majority for routine decisions; 2/3 supermajority for standard approval and Charter amendments
- Decisions are documented and published within 7 working days

**Transition to v1.0:** The Council composition will be expanded to include elected member representatives, with term limits and election procedures defined in v1.0.

### 3.2 Technical Secretariat

**Role:** The operational body responsible for day-to-day standards administration:
- Maintains the standards repository and document management system
- Coordinates Working Group activities and meeting schedules
- Assigns editors and reviewers for draft documents
- Manages public comment periods and tracks resolutions
- Publishes approved standards and maintains version histories
- Serves as the primary contact point for external inquiries

**Accountability:** The Secretariat reports to the Standards Council and operates under its direction.

### 3.3 Working Groups

Working Groups (WGs) are the primary forums for technical content development. Each WG has a defined scope, chair, and participant list.

**Current Working Groups:**

| Working Group | Scope | Chair (v0.5) |
|---|---|---|
| **DPP-CQ Technical WG** | Core specification, data models, credential formats, carrier specification | Technical Secretariat |
| **Governance & Compliance WG** | Governance framework, legal alignment, conformity assessment, privacy | Technical Secretariat |
| **Interoperability WG** | Integration with W3C, GS1, ISO, EU DPP, UNECE, and other standards bodies | Technical Secretariat |
| **Use Cases & Pilots WG** | Real-world implementation, case studies, sectoral adaptation, pilot coordination | Technical Secretariat |

**WG Operations:**
- **Meetings:** Bi-weekly (or as needed); open to all registered participants
- **Decision-making:** Consensus-seeking; if consensus cannot be reached, the WG chair makes a provisional decision subject to Council review
- **Documentation:** Meeting minutes published in the repository within 5 working days
- **Participation:** Open to any individual or organization; participants register by emailing info@icoun.org

**WG Lifecycle:**
1. **Proposal:** Any participant may propose a new WG by submitting a scope definition and rationale to the Secretariat
2. **Approval:** The Standards Council approves new WGs based on need and resource availability
3. **Operation:** Active WGs maintain a public charter, participant list, and work plan
4. **Closure:** WGs may be closed when their work is complete or when activity ceases; closure requires Council approval

---

## 4. Standards Development Process

All ICO standards follow a defined lifecycle with mandatory gates:

```
  Proposal → Working Draft → Committee Draft → Public Review → Final Standard
              (WD)              (CD)              (PR)            (IS)
```

### 4.1 Stage Descriptions

| Stage | Description | Duration | Approval Gate |
|---|---|---|---|
| **Proposal** | A scope and justification are submitted; Council approves the work item | — | Council |
| **Working Draft (WD)** | Developed within a WG; iterates based on WG discussion | Variable | WG consensus |
| **Committee Draft (CD)** | WG approves the draft for broader review; Secretariat assigns a document number | — | WG + Secretariat |
| **Public Review (PR)** | Published for public comment; minimum 45-day comment period | ≥ 45 days | Secretariat |
| **Final Standard (IS)** | All comments resolved; Council approves for publication | — | Council |

### 4.2 Public Review Requirements

Every standard must undergo at least one Public Review period before approval as a Final Standard. Requirements:
- **Minimum duration:** 45 calendar days
- **Publication:** The draft must be publicly accessible (GitHub + web portal)
- **Comment handling:** All comments must be logged, acknowledged, and either adopted or rejected with rationale
- **Re-review:** If substantive changes are made after the first review, a second review period may be required (determined by the Secretariat + WG chair)

### 4.3 Document Numbering

Approved standards are assigned an **ICO Std NNNN** identifier:
- **1000-series:** Base protocols (DID, VC, data traceability)
- **2000-series:** Product standards (DPP-CQ, GI, haute couture)
- **3000-series:** System & assessment standards (credibility assessment)
- **4000-series:** Governance & compliance standards

Draft documents use the format **ICO Std NNNN vX.Y.Z-draft** until approved as a Final Standard.

### 4.4 Maintenance and Revision

Published standards are maintained through:
- **Editorial corrections:** Typographical errors, clarifications (no substantive changes) — administered by Secretariat
- **Amendments:** Substantive changes require a new development cycle (WD → PR → IS)
- **Withdrawal:** Standards may be withdrawn by the Council if obsolete or unviable

---

## 5. Intellectual Property Policy

### 5.1 Licensing

- **Specifications, documentation, and white papers:** Creative Commons Attribution 4.0 International (CC BY 4.0)
- **Reference implementations and software:** Apache License, Version 2.0

### 5.2 Patent Policy (v0.5 — Placeholder)

Participants in the standards development process are expected to disclose any known patents that may be essential to implementing the standard. A formal Patent and Royalty-Free (RF) licensing policy will be defined in Governance Charter v1.0.

**Interim principle:** ICO standards are intended to be implementable on a royalty-free basis. If patented technology is included, the patent holder will be asked to provide a royalty-free license or reasonable, non-discriminatory (RAND) terms.

### 5.3 Contributor Agreement

For significant contributions (above a threshold determined by the Technical Committee), contributors may be asked to sign a Contributor License Agreement (CLA). This ensures the project has the necessary rights to distribute contributions.

---

## 6. Participation Pathways

| Pathway | Description | Requirements |
|---|---|---|
| **Community Contributor** | File issues, submit public comments, participate in discussions | None — open to all |
| **Working Group Participant** | Attend WG meetings, contribute to draft development | Registration via email |
| **Document Editor** | Lead authoring of specific standard documents | Appointed by WG + Secretariat |
| **WG Chair** | Lead a Working Group, facilitate consensus | Appointed by Council |
| **Standards Council Member** | Approve standards, set strategic direction | Appointed by Council (v0.5); elected (v1.0) |
| **Regional Node** | Operate a regional instance of the standards infrastructure | Partnership agreement with ICO |

---

## 7. Dispute Resolution

### 7.1 Internal Resolution

Disputes within Working Groups are resolved through:
1. **Discussion:** The WG chair facilitates discussion to reach consensus
2. **Escalation:** If consensus cannot be reached, the matter is escalated to the Technical Secretariat
3. **Council Review:** If the Secretariat cannot resolve the dispute, it is referred to the Standards Council for a binding decision

### 7.2 Appeals

Any participant may appeal a WG or Secretariat decision by:
1. Submitting a written appeal to the Secretariat within 30 calendar days of the decision
2. The appeal must describe the decision, the grounds for appeal, and the desired outcome
3. The Standards Council reviews the appeal and issues a decision within 30 calendar days

### 7.3 External Disputes

Disputes involving external parties (e.g., patent claims, licensing disputes) are handled by the ICO Executive Chairman in consultation with legal counsel, with the goal of resolving disputes amicably and in accordance with applicable law.

---

## 8. Amendment of This Charter

This Charter may be amended by:
1. **Proposal:** Any Standards Council member or WG participant may propose an amendment
2. **Review:** The proposed amendment is circulated for comment (minimum 14 days)
3. **Approval:** The Standards Council approves the amendment by 2/3 supermajority
4. **Publication:** The amended Charter is published with a version increment and change log

---

## 9. Transition Plan: v0.5 → v1.0

This v0.5 Charter is designed to be sufficient for the immediate needs of the DPP-CQ v2.0 public review and stabilization process. The following items will be addressed in the transition to v1.0:

| Item | v0.5 Status | v1.0 Target |
|---|---|---|
| Council composition | Founder-appointed | Elected member representatives |
| WG chairs | Secretariat-appointed | Elected or appointed with WG input |
| Patent policy | Placeholder (RF principle) | Formal RF or RAND policy |
| Election procedures | Not defined | Defined with term limits |
| Regional node framework | Conceptual | Formal partnership agreement template |
| Financial sustainability | Not addressed | Fee model for premium services (not for standard access) |
| Anti-trust compliance | Not addressed | Formal guidelines for participant conduct |

**Target timeline for v1.0:** Q1 2027, after the first cohort of Working Group participants has been established and initial standards have been published.

---

## 10. Contact

- **Governance inquiries:** info@icoun.org
- **Working Group participation:** info@icoun.org
- **GitHub repository:** https://github.com/ICO-cloud/dpp-cq-standard
- **Standards portal:** https://www.dppcq.org

---

*This Charter is published under the Creative Commons Attribution 4.0 International License (CC BY 4.0).*

*© 2026 International Communication Organization (ICO). All rights reserved.*
