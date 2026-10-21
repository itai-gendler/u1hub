---
kind: system
acts: external
references:
  - kind: code
    role: implementation
    target: core/health.js
  - kind: doc
    role: context
    target: README.md
---

# Watchdog

A service watchdog or home-lab uptime monitor that polls the Hub's health address with no sign-in.
