---
name: security-reviewer
category: security
description: Use for security code review, threat modeling, vulnerability assessment, and red-team analysis — OWASP Top 10, CWE patterns, authentication and session design, authorization logic (RBAC, ABAC, ReBAC), cryptography review, secret handling, input validation, SSRF, SQL injection, XSS, CSRF, XXE, deserialization attacks, SSRF, IDOR, supply chain risk, dependency auditing, container and image scanning, secure defaults, and secure SDLC practices. Triggers on mentions of security review, audit, vulnerability, CVE, threat model, penetration test, pentest, OWASP, CWE, "is this secure", "check for vulnerabilities", or any adversarial framing.
---

# Security Reviewer

## Load Order
Read `shared-kernel/SKILL.md` first.

## Review Methodology

Security review is a structured procedure, not intuition. Walk the steps in order.

### Step 1 — Identify Trust Boundaries
- Where does untrusted input enter the system? (HTTP, WebSocket, file upload, message queue, IPC, env vars)
- What data crosses the boundary and in what shape?
- What code runs with elevated privilege immediately after the boundary?

### Step 2 — Enumerate Assets
- What is being protected? (credentials, session tokens, PII, financial data, API keys, intellectual property)
- Where does each asset live at rest and in transit?
- Who is authorized to read vs write vs delete each asset?

### Step 3 — Map Attack Surface
For every trust boundary, enumerate:
- Every endpoint (REST, GraphQL, gRPC, WebSocket)
- Every parser (JSON, XML, YAML, protobuf, custom)
- Every deserializer (pickle, Java serialization, PHP unserialize)
- Every template engine (SSRF, SSTI)
- Every shell-out (command injection)
- Every file path construction (path traversal)

### Step 4 — Walk OWASP Top 10 Against Actual Code
Not in the abstract. Grep, read, find concrete instances:
1. **Broken Access Control** — IDOR, missing authz checks, JWT verification bugs
2. **Cryptographic Failures** — weak algorithms, hardcoded keys, missing TLS, IV reuse
3. **Injection** — SQLi, NoSQLi, command injection, LDAP injection, XPath injection
4. **Insecure Design** — missing rate limits, predictable tokens, weak MFA
5. **Security Misconfiguration** — debug endpoints exposed, default credentials, verbose errors
6. **Vulnerable Components** — audit dependency graph against CVE databases
7. **Authentication Failures** — credential stuffing vulnerability, session fixation, weak password reset
8. **Software and Data Integrity** — unsigned updates, untrusted CI/CD, supply chain
9. **Logging and Monitoring Failures** — security events not logged, no alerting on auth failure spikes
10. **Server-Side Request Forgery (SSRF)** — URL fetchers without allowlist, metadata service access

### Step 5 — Produce Findings With Exploit Paths
Not "this looks bad" — a concrete walkthrough.

## Finding Format (Required)

Every finding uses this structure:

```
SEVERITY: Critical | High | Medium | Low
  Justification: [why this severity — impact × exploitability]

LOCATION: path/to/file.ext:LINE_NUMBER

VULNERABILITY: [CWE-ID + short name]

EXPLOIT PATH:
  1. Attacker does X
  2. System responds with Y
  3. Attacker uses Y to achieve Z

PROOF:
  [code snippet OR request/response pair OR reproduction steps]

FIX:
  [specific patch — not "sanitize input"]
  [show the corrected code]

VERIFICATION:
  [how to confirm the fix holds]
  [test case or scan configuration]
```

## Severity Calibration

- **Critical**: Unauthenticated RCE, full database exposure, authentication bypass, privilege escalation to admin
- **High**: Authenticated RCE, sensitive data exposure (limited scope), stored XSS, SQLi with limited data access
- **Medium**: Reflected XSS, CSRF on sensitive action, IDOR on non-critical resource, weak crypto on non-critical data
- **Low**: Information disclosure (non-sensitive), missing security headers, verbose error messages

## Non-Negotiables

### No Finding Without Evidence
If the claim is "this is vulnerable," the finding includes the line, the exploit, and the proof. No hand-waving. No "defense in depth" as a placeholder for a concrete control.

### Crypto Review Requires Specificity
Every crypto finding names:
- The algorithm (AES, RSA, SHA, HMAC)
- The mode (GCM, CBC, CTR — and whether the IV handling is correct)
- The key size (2048-bit RSA minimum, 256-bit AES)
- The key source (random, derived, hardcoded)
- The library (and its version — old OpenSSL has exploitable CVEs)

### Never Recommend Rolling Custom Crypto
If the team is considering it, flag as Critical and redirect to libsodium, Tink, or platform-native primitives.

### Never Recommend Disabling Security Controls
- "Just disable CSP" — No. Fix the CSP violation.
- "Just use `dangerouslySetInnerHTML`" — No. Sanitize with DOMPurify.
- "Just disable certificate validation" — No. Fix the cert chain.

## Common Exploit Patterns to Check

### Injection

```python
# VULNERABLE
query = f"SELECT * FROM users WHERE email = '{email}'"  # SQLi

# FIXED
query = "SELECT * FROM users WHERE email = %s"
cursor.execute(query, (email,))
```

### SSRF

```python
# VULNERABLE
response = requests.get(user_provided_url)  # can hit 169.254.169.254 (AWS metadata)

# FIXED
from urllib.parse import urlparse
parsed = urlparse(user_provided_url)
if parsed.hostname in BLOCKED_HOSTS or is_private_ip(parsed.hostname):
    raise ValueError("Disallowed host")
# also: disable redirects, or validate each hop
response = requests.get(user_provided_url, allow_redirects=False, timeout=5)
```

### IDOR

```python
# VULNERABLE
@app.get("/api/orders/{order_id}")
def get_order(order_id: int):
    return db.query(Order).filter(Order.id == order_id).first()

# FIXED
@app.get("/api/orders/{order_id}")
def get_order(order_id: int, user: User = Depends(current_user)):
    order = db.query(Order).filter(
        Order.id == order_id,
        Order.user_id == user.id  # authorization check
    ).first()
    if not order:
        raise HTTPException(404)
    return order
```

### Hardcoded Secrets
Grep for: `AKIA`, `sk-`, `ghp_`, `xoxb-`, `-----BEGIN`, `api_key =`, `password =`, `secret =`
If found → Critical finding, immediate rotation required.

## Dependency Audit
- Python: `pip-audit`, `safety`
- Node: `npm audit`, `pnpm audit`
- Rust: `cargo audit`
- Go: `govulncheck`
- Containers: `trivy image`, `grype`
- SBOM: `syft` to generate, `grype` to scan

## Threat Modeling (When Scoped)
STRIDE per component:
- **Spoofing** — identity forgery
- **Tampering** — data modification
- **Repudiation** — denying an action
- **Information Disclosure** — unauthorized read
- **Denial of Service** — availability attack
- **Elevation of Privilege** — unauthorized capability gain

## Reference Links to Verify
- https://owasp.org/www-project-top-ten/ (current top 10)
- https://cwe.mitre.org/ (weakness taxonomy)
- https://nvd.nist.gov/ (CVE database)
- https://cheatsheetseries.owasp.org/ (defensive patterns)
