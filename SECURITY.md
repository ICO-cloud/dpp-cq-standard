# Security Policy

## Reporting a Vulnerability

The ICO DPP-CQ project takes security vulnerabilities seriously. We appreciate your efforts to responsibly disclose your findings.

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, please report them via email to:

- **info@icoun.org**

You should receive a response within 48 hours. If for some reason you do not, please follow up via email to ensure we received your original message.

## What to Include

When reporting a security issue, please include:

- Description of the vulnerability
- Steps to reproduce the issue
- Affected versions or components
- Potential impact
- Any suggested remediation (if available)

## Preferred Languages

We prefer all communications to be in English or Chinese (中文).

## Disclosure Policy

Our security disclosure process follows the standard practice of:

1. **Acknowledgement** — Confirm receipt of the report within 48 hours
2. **Assessment** — Evaluate the vulnerability and determine severity
3. **Remediation** — Develop and test a fix
4. **Release** — Deploy the fix and coordinate disclosure
5. **Acknowledgement** — Publicly credit the reporter (with permission)

We aim to respond to critical vulnerabilities within 7 days, and medium-severity issues within 30 days.

## Scope

This security policy applies to:
- DPP-CQ JSON Schema and reference implementations
- Root resolver network software
- SDKs and developer tools
- Official project documentation

**Out of scope:**
- Third-party implementations of DPP-CQ
- Issues in underlying cryptographic primitives (report directly to the relevant library maintainers)
- Social engineering attacks

## Security Considerations for Implementers

For organizations implementing DPP-CQ, please note:
- Always verify credential signatures against the issuer's DID document
- Use established cryptographic libraries — do not roll your own crypto
- Follow the threat model documented in the DPP-CQ specification
- Keep private keys in secure storage (HSMs or secure enclaves for production)

---

*Last updated: July 2026*
