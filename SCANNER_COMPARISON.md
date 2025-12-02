# Scanner Comparison

## Only CodeQL (SAST) Found

- Code patterns and logic errors in source code such as missing validation, unsafe flows.
- Issues like SQL injection risks arising from unsafe coding practices and string concatenation.
- Hardcoded secrets or credentials embedded in source.

## Only ZAP (DAST) Found

- Missing or misconfigured security headers (CSP, Strict-Transport-Security, Permissions-Policy).
- Runtime configuration problems such as HTTP-only sites, weak cache-control, or timestamp/banner disclosures.
- Findings reflected in scan alerts where headers or behaviors are not obvious from source code.

## Only Dependency-Check (SCA) Found

- Outdated third-party package versions with known CVEs.
- Supply chain risks from insecure or compromised libraries not detectable by source or runtime scans.

## Overlap Between Tools

- SCA issues may indirectly lead to runtime problems visible to DAST, but the root cause remains in the vulnerable dependency.
