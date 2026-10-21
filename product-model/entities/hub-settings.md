---
singleton: true
domain: settings
references:
  - kind: code
    role: implementation
    target: core/settings.js#publicCfg
  - kind: code
    role: implementation
    target: core/config.js#computeFeatures
---

# Hub settings

The settings the Hub keeps once for the whole farm, apart from the ones with a section of their own.

## Information kept

- **G-code folder** — The base folder of the Hub library (the slicer's output folder); each added printer type gets a subfolder of it.
- **Features** — Which feature modules are switched on; a change applies on the next Hub restart.
- **Affiliate links** — Whether the Replenish on Amazon links carry the project's affiliate tag; on until turned off.
- **Sell floor per gram** — The least a gram of print must sell for; 0.12 unless changed.
- **Filament cost per gram** — What a gram of filament costs; 0.02 unless changed.
- **Timelapse folder** — Where finished timelapse videos are saved; blank means none are made.
- **Update checks** — Whether the Hub checks once a day for a newer release; on unless turned off.
- **Latest version** — The newest release the last update check found.
