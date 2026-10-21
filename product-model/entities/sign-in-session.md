---
domain: settings
references:
  - kind: code
    role: implementation
    target: auth.js#signSession
  - kind: code
    role: implementation
    target: auth.js#verifySession
---

# Sign-in session

One browser's signed-in state while the Hub is password-protected. Sessions are not listed anywhere; they end by logging out, by expiring, or all at once.

## Information kept

- **Expires** — Thirty days after signing in or setting the password.
