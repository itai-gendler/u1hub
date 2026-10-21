---
singleton: true
domain: models
references:
  - kind: code
    role: implementation
    target: modules/models.js#explorerToken
---

# Models folder settings

What the Models tab reads and how it hands files to Snapmaker Orca, set under the tab's Folder panel.

## Information kept

- **Models folder** — The folder of 3MF project files, organized Designer, then Model, then file.
- **Orca location** — Where Snapmaker Orca is installed on the Hub computer.
- **U1 template** — The U1 project Convert to U1 takes its printer and filament presets from; u1_template.3mf at the top of the models folder unless a path is set.
- **Designer names** — Folder name to display name, one per line, to rename or merge designers without moving a file.
- **Pairing token** — The token 3MF Explorer sends with every print request.
