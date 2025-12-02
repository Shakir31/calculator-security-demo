# Security Scan Analysis - 2025-12-01

## DAST Results (ZAP Baseline)

- Total URLs scanned: 3 primary URLs (/, /favicon.ico, /robots.txt) plus sitemap and Firefox CDN resources.
- PASS: 63
- WARN-NEW: 2 Medium-risk warnings, 6 Low-risk warnings.
- FAIL-NEW: 0 critical failures (High-risk alerts).

### Warning Summary

- Medium Risk:
  - 10038: Content Security Policy (CSP) Header Not Set (5 instances)
  - 10106: HTTP Only Site (application served only via HTTP)
- Low Risk:
  - 90004: Insufficient Site Isolation Against Spectre Vulnerability
  - 10063: Permissions Policy Header Not Set
  - 10036: Server version information leaks (Werkzeug 3.1.3 / Python 3.9.25)
  - 10035: Strict-Transport-Security Header Not Set
  - 10096: Timestamp Disclosure - Unix
  - 10021: X-Content-Type-Options Header Missing
- Informational:
  - Various headers missing, cache control issues, and security fetch headers missing

## SCA Results (Dependency Check)

- High severity vulnerabilities exist due to intentionally outdated dependencies.
- Vulnerable packages include:
  - flask==2.0.1 (known CVEs)
  - werkzeug==2.0.1 (known CVEs)

## SAST Results (CodeQL)

- Total issues found: 0
- No detected code-level security issues.

## Recommendations

- **Add security headers**: Include Content Security Policy, Permissions Policy, and site isolation headers.
- **Upgrade dependencies**: Update flask and werkzeug to their latest secure versions.
