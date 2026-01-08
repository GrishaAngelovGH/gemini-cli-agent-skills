# Security Review Checklist

## 1. Input Validation & Sanitization
- [ ] Is all user-provided input validated against a strict allow-list?
- [ ] Are inputs sanitized before being used in HTML (XSS prevention)?
- [ ] Are inputs sanitized before being used in database queries (SQLi prevention)?
- [ ] Are inputs sanitized before being used in OS commands (Command Injection prevention)?

## 2. Authentication & Session Management
- [ ] Are passwords hashed using strong, modern algorithms (e.g., Argon2, bcrypt)?
- [ ] Is multi-factor authentication (MFA) used where appropriate?
- [ ] Are session tokens handled securely (HttpOnly, Secure, SameSite cookies)?
- [ ] Is there a secure logout and session timeout mechanism?

## 3. Sensitive Data Handling
- [ ] Are there any hardcoded secrets (API keys, passwords, tokens) in the code?
- [ ] Is sensitive data encrypted at rest and in transit (TLS 1.2+)?
- [ ] Are logs cleared of PII (Personally Identifiable Information) and secrets?

## 4. Access Control (Authorization)
- [ ] Does the code follow the Principle of Least Privilege?
- [ ] Are authorization checks performed on the server-side for every protected resource?
- [ ] Is there protection against Insecure Direct Object References (IDOR)?

## 5. Dependency Security
- [ ] Are third-party libraries up to date?
- [ ] Are there any known vulnerabilities (CVEs) in the project's dependencies?

## 6. Error Handling & Logging
- [ ] Do error messages avoid leaking stack traces or system information to the user?
- [ ] Is security-relevant information logged for auditing (without logging secrets)?

## 7. Common Web Vulnerabilities (OWASP Top 10)
- [ ] **Injection:** SQL, NoSQL, OS, and LDAP injection.
- [ ] **Broken Authentication:** Credential stuffing, session hijacking.
- [ ] **Sensitive Data Exposure:** Lack of encryption, weak keys.
- [ ] **XML External Entities (XXE):** Poorly configured XML processors.
- [ ] **Broken Access Control:** Escalating privileges.
- [ ] **Security Misconfiguration:** Default accounts, verbose error headers.
- [ ] **Cross-Site Scripting (XSS):** Reflected, Stored, or DOM-based.
- [ ] **Insecure Deserialization:** Executing code from untrusted data.
