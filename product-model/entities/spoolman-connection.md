---
singleton: true
domain: spools
references:
  - kind: code
    role: implementation
    target: modules/spoolman.js#mapSpool
---

# Spoolman connection

The link to an existing Spoolman inventory server, for importing rolls and, if wanted, recording the grams each print uses there too.

## Information kept

- **Spoolman address** — The Spoolman server's http or https address.
- **Write-back** — Whether the grams each finished print takes off an imported roll are also recorded in Spoolman; off unless ticked.
- **Last import** — When the last import ran and what it did.
