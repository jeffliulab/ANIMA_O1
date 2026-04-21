# Security Policy

## This project is a research prototype

**ANIMA is NOT a safety-certified system.** It is an open-source research prototype of a cognitive framework. Applications that build on ANIMA for safety-critical domains (medical, industrial, automotive) must carry out their own validation and certification; do not deploy ANIMA itself in clinical or production-safety settings.

## Reporting a vulnerability

If you believe you have found a security issue or a defect with **safety implications** (for example: a way to bypass Test-and-Check gates, inject malicious TaskSpecs, or cause the framework to emit unsafe motor commands), please **do not open a public GitHub issue**.

Instead, email the maintainer privately:

- **Contact**: the email address listed under `project.authors` in [`pyproject.toml`](./pyproject.toml)
- **Subject line**: `[SECURITY] anima: <short summary>`
- **PGP**: not yet available; an encrypted channel can be arranged on request

You should receive an acknowledgement within **72 hours**. A triage and remediation plan will follow within **7 days**.

## What to include

- Description of the issue and its impact
- Steps to reproduce (a minimal test case is very helpful)
- Affected version / commit SHA
- Whether you believe the issue has safety implications for downstream applications, and why

## Disclosure policy

- We follow **coordinated disclosure**: we ask reporters to withhold public disclosure until we have a fix available or 90 days have elapsed, whichever comes first.
- We will credit reporters in the CHANGELOG unless they request anonymity.
- For issues with downstream safety implications, we may extend the disclosure window if an integrator needs time to patch.

## Scope

Security reports welcomed for:

- The framework source code in `src/anima/`
- LLM provider abstractions and tool-calling paths
- Test-and-Check validation logic
- E-stop handling in adapter protocols
- Dependencies declared in `pyproject.toml`

Out of scope:

- Issues in third-party dependencies that are already publicly known and awaiting upstream patch
- Social engineering or physical-security scenarios
- Performance / denial-of-service on reference deployments (not safety-critical)

## Supported versions

| Version | Supported |
|---------|-----------|
| 0.1.x (alpha) | ✅ main branch |
| < 0.1.0 | ❌ |
