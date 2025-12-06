# Architecture Overview

## 1. System Architecture
The Secure Authentication System is composed of:

- **Frontend (React)**: registration, login, TOTP input
- **Backend (Node.js)**: authentication logic, JWT creation, TOTP verification
- **Database**: user table containing:
  - email
  - hashed_password
  - totp_secret
  - isActive
- **Security Modules**:
  - bcrypt for hashing
  - jsonwebtoken for access/refresh tokens
  - speakeasy for TOTP

## 2. Component Overview
- **AuthController**: handles login, register, refresh
- **Crypto Module**: hashing, token signing, TOTP
- **Session Manager**: managing refresh tokens
- **DB Layer**: user creation & lookup

## 3. Data Flow
### Registration:
User → Frontend → Backend → Hash Password → Store User → Generate TOTP QR → Success

### Login:
User → Backend → Verify password → Verify TOTP → Generate JWT → Send tokens

### Refresh:
Client → Backend → Verify refresh token → Issue new JWT

## 4. Technologies Used
- Node.js / Express
- JWT
- Speakeasy (TOTP)
- bcrypt
- React frontend
