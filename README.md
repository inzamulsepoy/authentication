# Authentication Demo

A small frontend demo that showcases two authentication flows:

- A sign-up popup (email / password) with client-side validation and a password strength meter.
- Google Sign-In integration (Google Identity Services) with a demo UI to show profile info.

Built as a simple local demo for learning and prototyping — **not** production-ready.

---

## 🔧 Files

- `index.html` — Sign-up popup (email/password) demo with localStorage persistence (`demo_users`).
- `index1.html` — Google Sign-In demo (Google Identity Services) with a navbar (Sign in / Sign up) and a sign-up modal.

---

## 🚀 Quickstart

1. Open the files in your browser (double-click or use a local server):
   - Recommended: run a local server from the project folder:
     ```bash
     python -m http.server 8000
     # open http://localhost:8000/index1.html
     ```
2. Replace the placeholder Google Client ID in `index1.html`:
   ```js
   const CLIENT_ID = 'REPLACE_WITH_GOOGLE_CLIENT_ID.apps.googleusercontent.com';
   ```
3. Test flows:
   - Use the **Sign up** navbar button to open the sign-up popup and register demo users (saved in `localStorage` under `demo_users`).
   - Use the **Sign in** navbar button (renders Google button) to authenticate via Google after you configure the client ID.

---

## ✅ Features

- Accessible modal with focus management and keyboard controls (Esc, Tab trap)
- Client-side validation for email, password length, and matching confirm password
- Password strength meter
- Stores demo users in `localStorage` for demonstration
- Google Identity Services (GSI) integration and simple ID token parsing for demo

---

## ⚠️ Security & Production Notes

- **Do not** trust client-side token parsing for authentication. Always verify Google ID tokens server-side.
- Do not store sensitive tokens or passwords in `localStorage` for production use.
- Use HTTPS, secure cookies, and server-side session management for real auth flows.
- Consider using the official Google libraries and server-side verification (or use Firebase Auth) for production readiness.

Server-side verification example (Node + express):
```js
// POST /auth/google
// Verify ID token server-side using @google-auth-library
const {OAuth2Client} = require('google-auth-library');
const client = new OAuth2Client(CLIENT_ID);
const ticket = await client.verifyIdToken({ idToken: token, audience: CLIENT_ID });
const payload = ticket.getPayload();
// payload contains verified profile fields
```

---

## 📈 Next steps (suggested)

- Add a minimal backend endpoint (Node/Express) to verify ID tokens and create sessions.
- Add server-side user persistence (database) and secure password storage (bcrypt).
- Add CI for linting and tests, and a small integration test for flows.
- Add other OAuth providers (GitHub) or One Tap integration.

---

## 📄 License

MIT — feel free to reuse and adapt for learning and prototypes.

---

If you'd like, I can add a sample Node/Express verification endpoint or wire a simple API to persist users — tell me which backend stack you prefer and I'll implement it. ✨
