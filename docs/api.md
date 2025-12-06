# API Documentation

Base URL: http://localhost:5000

---

## 1. Register User
### POST /api/register
Registers a new user.

### Request Body:
{
  "email": "string",
  "password": "string"
}

### Response:
{
  "message": "User registered",
  "totp_secret": "Base32 secret for Google Authenticator"
}

---

## 2. Login (Password Only)
### POST /api/login
Checks email + password and prompts for TOTP.

### Request Body:
{
  "email": "string",
  "password": "string"
}

### Response:
{
  "message": "Password OK, enter TOTP"
}

---

## 3. Verify TOTP
### POST /api/verify-totp

### Request Body:
{
  "email": "string",
  "totp": "123456"
}

### Response:
{
  "accessToken": "jwt",
  "refreshToken": "jwt"
}

---

## 4. Refresh Token
### POST /api/refresh-token

### Request Body:
{
  "refreshToken": "string"
}

### Response:
{
  "accessToken": "newAccessToken"
}

---

## 5. Protected Route Example
### GET /api/protected

Headers:
Authorization: Bearer ACCESS_TOKEN

### Response:
{
  "message": "Protected data"
}

