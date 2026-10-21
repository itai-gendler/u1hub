---
scope: The U1 Print Hub server, its browser pages and feature modules at the pinned source revision.
method: Static reading of the server, modules, browser pages, README and changelog; nothing was run.
covered:
  - description: Sign-in, access modes and the Cloudflare tunnel.
    paths:
      - auth.js
      - tunnel.js
      - public/auth.html
  - description: 'Core server: settings, printer types, the library and printer files, Up next, sending and controlling prints, the fleet and its events, print history, health and diagnostics.'
    paths:
      - server.js
      - core/
      - parser.js
  - description: Spool identity, tags, loadout and the filament library.
    paths:
      - rfid.js
      - filament-swatches.json
      - scripts/refresh-filament-db.js
      - public/labels.html
  - description: 'Feature modules: Dispatch, Resources, Spoolman, phone notifications, AI pre-flight, Models, worth printing, Logbook, timelapses, updates, cameras, smart plugs and printer pages.'
    paths:
      - modules/dispatch.js
      - modules/resources.js
      - modules/spoolman.js
      - modules/notify.js
      - modules/advisor.js
      - modules/models.js
      - modules/margin.js
      - modules/logbook.js
      - modules/timelapse.js
      - modules/updates.js
      - modules/camera.js
      - modules/power.js
      - modules/klipper.js
      - modules/spools.js
      - modules/desktop.js
      - modules/u1convert.js
      - modules/tuning.js
      - modules/mesh3mf.js
  - description: The dashboard page, its script, stylesheet and the browser half of each module.
    paths:
      - public/index.html
      - public/app.js
      - public/gold.css
      - public/sw.js
      - public/manifest.json
      - public/modules/dispatch-ui.js
      - public/modules/resources-ui.js
      - public/modules/spoolman-ui.js
      - public/modules/notify-ui.js
      - public/modules/advisor-ui.js
      - public/modules/models-ui.js
      - public/modules/margin-ui.js
      - public/modules/logbook-ui.js
      - public/modules/timelapse-ui.js
      - public/modules/updates-ui.js
exclusions:
  - description: Tests, the test harness and its mock printers.
    paths:
      - test/
  - description: Developer and release scripts, CI, packaging and container files.
    paths:
      - scripts/boot-4546.cmd
      - scripts/bump-version.js
      - scripts/check-core.js
      - scripts/check-index-js.js
      - scripts/check-version.js
      - scripts/contrast-audit.js
      - scripts/failscan.js
      - scripts/falsify-matchmaint.js
      - scripts/falsify-reconcile.js
      - scripts/falsify-replenish.js
      - scripts/gate-dispatch.js
      - scripts/gate-klipper.js
      - scripts/gate-spoolman.js
      - scripts/gate-timelapse.js
      - scripts/grepcss.js
      - scripts/loopprof.js
      - scripts/open-on-desktop.ps1
      - scripts/pack-tester-zip.js
      - scripts/peek-access.js
      - scripts/peek-gcode-store.js
      - scripts/peek-tab-traffic.js
      - scripts/restart-4545.cmd
      - scripts/run-harness.cmd
      - scripts/seed-4546.js
      - scripts/shoot-docs.js
      - scripts/smoke-resources.cmd
      - scripts/split-app.js
      - scripts/split-core.js
      - scripts/stop-4546.cmd
      - .github/
      - Dockerfile
      - docker-compose.yml
      - .dockerignore
      - package.json
      - package-lock.json
      - start-mac-linux.sh
      - start-windows.bat
      - update.json
      - config.example.json
  - description: Documentation, screenshots, fonts, icons and vendored libraries.
    paths:
      - docs/
      - README.md
      - BETA-TESTING.md
      - LICENSE
      - public/fonts/
      - public/vendor/
      - public/favicon-32.png
      - public/favicon.svg
      - public/icon-192.png
      - public/icon-512.png
      - sf3d-logo.png
      - gcode/
  - description: A developer tool that captures how the slicer sends the head mapping.
    paths:
      - capture-proxy.js
unmapped:
  - description: Full Spectrum mix planner and recommender code (a page of its own beside the tabs), not yet described.
    paths:
      - fs-colors.js
      - public/fs-colors.html
      - modules/mixer.js
  - description: In-app slicing code, which ships switched off and is described as not ready.
    paths:
      - modules/slicing.js
      - public/modules/slicing-ui.js
      - slicer-template.3mf
  - description: 'Telemetry code behind the Dash drawers: farm totals, recent history, temperature trends and per-printer job stats, not yet described.'
    paths:
      - core/telemetry.js
  - description: Network inventory code for DHCP reservations, not yet described.
    paths:
      - core/network.js
  - description: Hidden developer routes that watch a printer's websocket traffic, with no page of their own.
    paths:
      - core/network.js
  - description: Timelapse storefront upload code, configured only by hand in config.json.
    paths:
      - modules/timelapse.js
  - description: Nightly state-file copies and the Hub log, with no page of their own.
    paths:
      - core/health.js
      - core/log.js
  - description: Worth-printing table code for removing a row and exporting CSV, small controls not yet described.
    paths:
      - modules/margin.js
      - public/modules/margin-ui.js
  - description: Spoolman connection test and write-back retry code, small controls not yet described.
    paths:
      - modules/spoolman.js
      - public/modules/spoolman-ui.js
  - description: Dispatch code for removing a bundle, clearing a job notice and undoing a push-back, small controls not yet described.
    paths:
      - modules/dispatch.js
      - public/modules/dispatch-ui.js
  - description: Resources code for Assume empty and forgetting leftover inventory, not yet described.
    paths:
      - modules/resources.js
      - public/modules/resources-ui.js
  - description: Printer type editing code (name and accent color), not yet described.
    paths:
      - core/library.js
      - public/app.js
  - description: Trusted-proxy list code in Settings, not yet described.
    paths:
      - auth.js
      - public/app.js
  - description: AI key test and notification test code, small controls not yet described.
    paths:
      - modules/advisor.js
      - modules/notify.js
  - description: Models code for unlinking a gcode, dismissing an Orca session and clearing a print request, not yet described.
    paths:
      - modules/models.js
      - public/modules/models-ui.js
  - description: Update check switch and dismissal code, not yet described.
    paths:
      - modules/updates.js
      - public/modules/updates-ui.js
limitations: []
---

# Coverage
