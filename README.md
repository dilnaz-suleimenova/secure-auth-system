# Secure Authentication System  
Multi-factor authentication system implementing Password + TOTP + JWT for strong user security.  
You can see the presentation in link: https://www.canva.com/design/DAG6tzzOEeY/RwC4W6IRQnwqPZExmbN4Fg/edit?utm_content=DAG6tzzOEeY&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
And documentation in /docs folder (you can read description in Documentation part below)
---

## Overview

This project implements a **secure, modern authentication system** that protects user accounts using:
- Strong password hashing (bcrypt)
- Time-based One-Time Passwords (TOTP) using Google Authenticator
- JWT-based access + refresh tokens
- Input validation and robust error handling
- Secure session management

The system includes a **React frontend**, **Node.js backend**, and a full set of **cryptographic modules + security analysis documentation**.

---

## 👥 Team Members & Responsibilities

| Name | Role | Responsibilities |
|------|------|------------------|
| **Temirlan Maksat** | Security Engineer | Threat modeling, vulnerability analysis, cryptographic verification, security design |
| **Suleimenova Dilnaz** | Backend Developer | API implementation, auth logic, JWT/TOTP integration, database layer |
| **Amangeldiyev Aidos** | Frontend Developer | UI development, login/register flow, form validation |

---

## Key Features

### **1. Authentication**
- Secure password hashing (bcrypt with salt)
- TOTP-based MFA (Google Authenticator)
- JWT access & refresh tokens
- Token rotation and expiration

### **2. Security**
- Input validation and sanitization
- Protected routes (JWT verification middleware)
- HttpOnly cookies (optional)
- No plaintext credentials stored
- Unique TOTP secret per user

### **3. Code Quality**
- Modular codebase (crypto, utils, routes)
- Unit tests for core functionality
- Error handling for all endpoints

### **4. Documentation**
- `architecture.md` → full system design  
- `security.md` → threat model + vulnerabilities + mitigation  
- `api.md` → all endpoints  
- `user_manual.md` → system usage guide  

---

## Project Structure
secure-auth-system/
│
├── README.md
├── LICENSE
├── .gitignore
├── package.json / package-lock.json
│
├── src/
│ ├── backend/ # Node.js backend logic
│ ├── frontend/ # React UI
│ ├── crypto/ # Cryptographic primitives
│ ├── utils/ # Helpers, validators
│ └── tests/ # Unit tests
│
└── docs/
├── architecture.md
├── security.md
├── api.md
└── user_manual.md

---

## Installation

### **1. Clone the repository**

git clone https://github.com/dilnaz-suleimenova/secure-auth-system.git

cd secure-auth-system


### **2. Install backend dependencies**
cd ../frontend
npm install


---

## Running the Project

### **Start the backend**
cd src/backend
npm start

### **Start the frontend**
cd src/frontend
npm start

The UI will be available at:  
`http://localhost:3000`

The backend will run at:  
`http://localhost:5000`

---

## API Usage Example

### **Login Request**
POST /login
Content-Type: application/json
{
"email": "user@example.com
",
"password": "mypassword",
"totp": "123456"
}

### **Response**

{
"accessToken": "...",
"refreshToken": "..."
}


More examples available in **docs/api.md**.

---

## Security Mechanisms

### Password Hashing
- bcrypt with salt
- Adaptive cost factor

### TOTP MFA
- RFC 6238 compliant TOTP
- Works with Google Authenticator

### JWT Tokens
- Access token (short lifetime)
- Refresh token (rotated)
- HMAC SHA-256 signing

---

## Documentation

All documentation is located in the `docs/` folder:

| File | Description |
|------|-------------|
| **architecture.md** | System architecture, components, data flow |
| **security.md** | Threat model, vulnerabilities, mitigations |
| **api.md** | API endpoints with examples |
| **user_manual.md** | Instructions for user registration, login, TOTP setup |

---

## Unit Tests

Basic unit tests exist for:
- Password hashing
- JWT verification
- TOTP verification
- Auth endpoints

Run:
npm test

## License

This project is licensed under the **MIT License**.  
See `LICENSE` for full text.

---

