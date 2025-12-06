# Architecture Documentation

## 1. System Overview
The Secure Authentication System is a web-based MFA (multi-factor authentication) platform that uses:
- Password hashing (bcrypt)
- TOTP verification (Google Authenticator)
- JWT Access + Refresh tokens

The system ensures strong authentication by combining something the user knows (password) and something the user has (TOTP code). The architecture consists of:

1. **Frontend (React)** – UI for registration, login, and TOTP input.
2. **Backend (Node.js)** – authentication logic, hashing, token signing, TOTP verification.
3. **Database** – stores hashed passwords and TOTP secrets.

---

## 2. Component Overview

### **Frontend (React)**
- Registration form (email + password)
- Login form
- TOTP code input
- Sends API requests to backend
- Displays TOTP secret (Base32) for manual entry in Google Authenticator

### **Backend (Node.js + Express)**
Handles:
- Password hashing using bcrypt
- TOTP secret generation
- TOTP code verification (6-digit, 30-second window)
- JWT token issuing (access + refresh tokens)
- Validation and secure error responses

### **Database**
Stores:
- email  
- hashed password  
- TOTP secret (Base32)  
- isActive flag  
- optional refresh token

No plaintext passwords or sensitive data is stored.

---

## 3. Data Flow

### **Registration Flow**
User → Frontend → Backend
├ Hash password (bcrypt)
├ Generate TOTP secret (Base32)
├ Store user in DB
└ Return Base32 secret to user

User manually enters the TOTP secret into Google Authenticator.

### **Login Flow**
User → Frontend → Backend
├ Verify password using bcrypt.compare()
├ Verify TOTP using speakeasy.totp.verify()
└ Issue JWT access + refresh tokens

### **Token Refresh Flow**
Frontend → Backend
├ Send refresh token
└ Receive new access token

---

## 4. Architecture Diagram (Text Format)
┌────────────┐ HTTP ┌──────────────┐ ┌──────────────┐
│ Frontend │ ───────────▶│ Backend │────▶│ Database │
│ React │ │ Node.js API │ │ User Records │
└────────────┘ └──────────────┘ └──────────────┘
│ Crypto Engine:
│ • bcrypt
│ • TOTP
▼ • JWT
User

---

## 5. Technologies Used
- **React.js** (UI)
- **Node.js + Express** (API)
- **bcrypt** (password hashing)
- **speakeasy** (TOTP)
- **jsonwebtoken** (JWT)

