---
availability:
  - place: hub::dashboard
domain: resources
references:
  - kind: code
    role: implementation
    target: modules/resources.js#buyLink
  - kind: code
    role: implementation
    target: modules/resources.js#isAmazonUrl
  - kind: code
    role: implementation
    target: modules/resources.js#affiliateConf
---

# Replenish on Amazon

The Replenish on Amazon button on a Resources row or a spool: the spool's own buy link, or an Amazon search for that exact filament.
