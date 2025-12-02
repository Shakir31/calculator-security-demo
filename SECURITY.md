# Security Scanning

## Overview

This repository uses three types of security scanning:

### SAST (Static Analysis with CodeQL)

- Scans the source code for security vulnerabilities without running the application.
- Runs automatically on every push or pull request to the `main` or `master` branch.
- Checks for code-level issues such as:
  - Code injection vulnerabilities
  - Hardcoded secrets and sensitive data
  - Insecure configurations
  - OWASP Top 10 security risks
- Results are available in the GitHub Security tab under Code scanning alerts.

### SCA (Dependency Check with OWASP Dependency-Check)

- Scans project dependencies listed in `requirements.txt` for known vulnerabilities and outdated packages.
- Runs automatically on every push or pull request to the `main` or `master` branch, after SAST completes.
- Checks for:
  - Known CVEs in Python packages (and other dependencies if present)
  - License compliance issues (where applicable)
- Generates detailed dependency vulnerability reports.
- Reports are uploaded as artifacts named `sca-reports`.

### DAST (Live Application Testing with OWASP ZAP)

- Dynamically tests the running application by simulating attacks on the live instance.
- Runs automatically on every push or pull request to the `main` or `master` branch, after the application is built successfully.
- Checks for runtime vulnerabilities including:
  - SQL injection and cross-site scripting (XSS)
  - Missing security headers and misconfigurations
  - Broken authentication or session management issues
- Produces two types of scan results:
  - Baseline scan (passive, fast)
  - Full scan (active, more thorough)
- Scan reports are uploaded as artifacts named `zap-baseline-reports` and `zap-fullscan-reports`.

## Understanding Results

- The scan results can be viewed in the Actions tab for detailed logs and artifact downloads.
- The Security tab in GitHub shows aggregated CodeQL alerts and dependency alerts.
- Severity levels help prioritize issues:
  - Critical and High: Address immediately to prevent exploits.
  - Medium: Plan fixes soon.
  - Low and Informational: Monitor or fix when possible.
- DAST results include categories such as PASS, WARN, FAIL with detailed issue codes for actionable remediation.

## Reporting Vulnerabilities

Please email security@example.com

## Workflow Files

- SAST: `.github/workflows/1-sast-only.yml` and `.github/workflows/4-complete-security.yml` (job: sast)
- SCA: `.github/workflows/2-sca-only.yml` and `.github/workflows/4-complete-security.yml` (job: sca)
- DAST: `.github/workflows/3-dast-only.yml` and `.github/workflows/4-complete-security.yml` (job: dast)
