---
appliesTo:
  - type: capability
    id: replenish-filament
  - type: capability
    id: turn-off-affiliate-links
  - type: capability
    id: turn-on-affiliate-links
references:
  - kind: code
    role: implementation
    target: modules/resources.js#buyLink
  - kind: code
    role: implementation
    target: modules/resources.js#isAmazonUrl
---

# The affiliate tag rides only on Amazon links, and only while on

With affiliate links on, an Amazon product link or search carries the project's tag; a link to any other shop is opened exactly as typed. Off means no tag on anything; the links still work.
