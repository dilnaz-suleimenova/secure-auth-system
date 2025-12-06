# User Manual

## 1. Registration
1. Go to the registration page.
2. Enter your email and password.
3. Submit the form.
4. The backend returns a **TOTP secret (Base32)**.
5. Open Google Authenticator.
6. Tap **+ → Enter setup key**.
7. Paste the Base32 code exactly.
8. Save the entry – you will now see a 6-digit code that refreshes every 30 seconds.

---

## 2. Login
1. Go to login page.
2. Enter email and password.
3. If the password is correct, the system asks for a TOTP code.
4. Open Google Authenticator.
5. Enter the current 6-digit code.

If correct:
- You receive an access token
- You receive a refresh token

---

## 3. Token Refresh
- When the access token expires, the frontend sends the refresh token.
- Backend verifies it and returns a new access token.

---

## 4. Troubleshooting

### “Invalid TOTP”
- Ensure your phone time is synced automatically
- Re-check Base32 code
- Wait for the next 30-second cycle

### “Password incorrect”
- Double-check your credentials

### “No code appears in Google Authenticator”
- Ensure Base32 secret is typed EXACTLY as given
