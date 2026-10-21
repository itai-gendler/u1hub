---
type: web
actors:
  - visitor
  - farm-operator
entryPoints:
  - web: /
  - web: /auth.html
languages:
  - en
references:
  - kind: code
    role: implementation
    target: core/app.js
  - kind: code
    role: implementation
    target: public/index.html
  - kind: code
    role: implementation
    target: public/app.js
  - kind: doc
    role: intent
    target: README.md
---

# U1 Print Hub

The Hub's web app, opened like a web page from any browser or phone on the Hub's network, or from anywhere through the tunnel. It can be added to a phone's home screen. Everything the Hub does for a person happens here.
