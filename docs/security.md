# Security Analysis

## 1. Threat Model
Potential threats include:
- Password brute force attacks
- Token theft
- Replay attacks
- Database leaks
- MITM attacks
- TOTP code interception

## 2. Security Assumptions
- HTTPS is always used
- Secrets are stored encrypted
- JWT tokens are short-lived

## 3. Vulnerabilities & Mitigation

### Weak Passwords
Mitigation:
- Minimum password rules
- bcrypt hashing

### Token Stealing
Mitigation:
- HttpOnly cookies
- Token rotation
- Short expiration times

### Replay Attacks
Mitigation:
- TOTP changes every 30 seconds
- Nonce used on refresh tokens

### DB Leak
Mitigation:
- Salted bcrypt hashes
- No plain-text TOTP secrets
