# OWASP A02: Cryptographic Failures — Recap

## Overview
**OWASP A02: Cryptographic Failures** refers to vulnerabilities that occur when sensitive data is **not properly protected using cryptography**. This includes failing to encrypt data, using weak or outdated algorithms, improper key management, or misconfiguring cryptographic mechanisms.

This category emphasizes **the protection of sensitive data**, rather than cryptographic theory itself.

> In previous OWASP editions, this category was known as *Sensitive Data Exposure*.

---

## What Is Sensitive Data?
Sensitive data commonly impacted by cryptographic failures includes:

- User passwords
- Session tokens and API keys
- Personally Identifiable Information (PII)
- Financial and payment data
- Authentication credentials

---

## Common Causes of Cryptographic Failures

- Storing sensitive data in plaintext
- Using weak or deprecated algorithms (e.g., MD5, SHA-1, DES)
- Improper password hashing techniques
- Missing or weak encryption for data in transit
- Hardcoded or poorly managed cryptographic keys
- Predictable random number generation
- Exposing secrets through logs, URLs, or error messages

---

## Real-World Examples

- Passwords hashed using fast algorithms like SHA-1
- Credit card data stored unencrypted in a database
- JWTs signed with weak or leaked secrets
- Applications allowing HTTP instead of HTTPS
- Mobile apps that disable certificate validation

---

## Impact
Successful exploitation of cryptographic failures can result in:

- Account takeover
- Identity theft
- Financial fraud
- Regulatory violations (GDPR, HIPAA, PCI-DSS)
- Loss of user trust and reputational damage

---

## Mitigation Strategies

### 1. Use Strong, Modern Cryptographic Algorithms
Only use industry-approved and well-supported algorithms:

- AES-256 for symmetric encryption
- RSA-2048+ or Elliptic Curve Cryptography (ECC) for key exchange
- SHA-256 or stronger for integrity validation

Avoid deprecated algorithms such as MD5, SHA-1, DES, and RC4.

---

### 2. Secure Password Storage
Passwords must be hashed using **slow, adaptive hashing algorithms** designed for password protection:

- Argon2id (preferred)
- bcrypt
- scrypt

Each password hash should include a unique salt to prevent rainbow table attacks.

---

### 3. Protect Data in Transit
All sensitive data must be transmitted securely:

- Enforce HTTPS everywhere
- Use TLS 1.2 or TLS 1.3 only
- Disable insecure protocols and ciphers
- Enable HTTP Strict Transport Security (HSTS)

---

### 4. Proper Key and Secret Management
Cryptographic keys and secrets must be handled securely:

- Never hardcode secrets in source code
- Store secrets in environment variables or secure vaults
- Rotate keys regularly
- Restrict access using least privilege

---

### 5. Minimize Sensitive Data Exposure
Reduce risk by limiting what data is stored or exposed:

- Do not store sensitive data unnecessarily
- Encrypt sensitive data at rest
- Mask or redact secrets in logs and error messages
- Avoid sending sensitive data in URLs

---

### 6. Use Trusted Cryptographic Libraries
Developers should rely on **well-maintained cryptographic libraries** and frameworks rather than implementing custom cryptographic logic.

> “Do not roll your own crypto.”

---

## 87. Hands-On Validation Using Replit (Prompt-Driven Simulation)

To reinforce mitigation concepts for OWASP A02, I enhanced the Replit application built in week 1 to create an educational application that contrasts insecure cryptographic practices with secure implementations of password hashing, key management, and data protection.

### Goals

- Demonstrate how insecure cryptographic practices lead to data exposure and account compromise (e.g., weak password hashing, poor key management, missing TLS).
- Show how proper cryptographic controls prevent exploitation (modern password hashing, secure key storage, encrypted transport).
- Provide an “ideal interaction” flow where users can:
  1. Submit sensitive data or credentials  
  2. Observe how insecure cryptographic handling fails  
  3. Toggle secure cryptographic protections  
  4. Observe safe, hardened behavior  


### Prompt You Can Use in Replit AI (Copy/Paste)
Added additional prompt "add an option to also test cyrptographic failures and protection".  

## Conclusion
Cryptographic failures represent a critical risk because they directly expose sensitive data to attackers, often at large scale and with minimal effort once data is obtained. Weak algorithms, improper password handling, poor key management, and misconfigured transport security can transform minor data exposure into full account compromise, financial fraud, and regulatory violations.

Preventing OWASP A02 vulnerabilities requires more than simply enabling encryption. Organizations must apply strong, modern cryptographic standards, manage keys and secrets securely, enforce encrypted communication, and minimize the storage and exposure of sensitive data. When cryptography is implemented correctly and consistently, it serves as a foundational defense that significantly reduces the impact of other application vulnerabilities.
