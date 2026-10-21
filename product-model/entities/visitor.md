---
kind: person
acts: external
references:
  - kind: code
    role: implementation
    target: auth.js
  - kind: code
    role: implementation
    target: public/auth.html
---

# Visitor

Someone who reaches the Hub without a session while it is password-protected. A visitor can only sign in; once signed in they are the Farm operator.
