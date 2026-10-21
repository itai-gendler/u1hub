---
availability:
  - place: hub::dashboard
domain: resources
references:
  - kind: code
    role: implementation
    target: modules/resources.js#affiliateConf
  - kind: code
    role: implementation
    target: public/app.js#loadAffiliateUI
---

# Turn off affiliate links

The switch, on the Resources tab and in Settings under Supporting the project, that sends Replenish on Amazon links out without the project's affiliate tag.
