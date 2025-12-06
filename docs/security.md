# Security Analysis

## 1. Threat Model

### 1.1 Phishing
Attackers try to steal user credentials through fake login pages.
**Mitigation:** MFA with TOTP prevents login even if password is stolen.

### 1.2 Brute-force Attacks
Attackers try many password combinations.
**Mitigation:** bcrypt hashing (slow, salted, expensive to brute force).

### 1.3 Token Theft
Attackers try to steal JWT tokens.
**Mitigation:**
- Short-lived access tokens
- Secure refresh token rotation
- JWT signature validation (HMAC-SHA256)

### 1.4 Replay Attacks
Attackers attempt to reuse previously captured codes.
**Mitigation:** TOTP rotates every 30 seconds; JWT tokens expire.

### 1.5 Database Exposure
If the database leaks, plaintext credentials must NOT be visible.
**Mitigation:**
- bcrypt-hashed passwords
- Base32 TOTP secrets (non-reversible)
- No sensitive secrets returned after registration

---

## 2. Vulnerabilities & Mitigation

### Weak Passwords
- Enforced password policy
- Hashing prevents storing raw passwords

### Incorrect TOTP Entry
- Clear user instructions
- TOTP verification uses 1-step time window

### Token Manipulation
- JWT signatures prevent tampering
- Tokens expire and refresh tokens can be invalidated

### Man-in-the-Middle (MITM)
- Use of HTTPS recommended in production

---

## 3. Summary of Security Strengths
- Strong salted hashing (bcrypt)
- MFA using TOTP (RFC 6238)
- Secure JWT token model
- Database stores no reversible secrets
- Resistant to brute-force, phishing, replay attacks, and token theft
