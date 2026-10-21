---
kind: primary
routes:
  web: Web
steps:
  - text: A U1 starts printing, with Timelapses on and a folder set
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Printing file
      - entity: hub-settings
        effect: reads
        facts:
          - Timelapse folder
      - entity: timelapse
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::timelapses
  - text: The Product starts a timelapse and grabs a fresh chamber-camera frame each time a new layer starts
    kind: product
    entities:
      - entity: timelapse
        effect: creates
        to: Recording
        facts:
          - Printer name
          - File
          - Started
          - Frames
    contexts:
      web:
        place: hub::dashboard::timelapses
  - text: The print completes
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::timelapses
  - text: The Product drops dark and repeated frames, turns the rest into a short video and saves it in the folder, named after the printer, the file and the time
    kind: product
    entities:
      - entity: timelapse
        effect: changes
        from: Recording
        to: Saved
        facts:
          - Video
          - Frames
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::timelapses
---

# A print becomes a video

## Trigger

A print starts on a U1.

## Outcome

The video is in the folder and listed as recent on the Timelapses card.

## Edge cases

- A Hub restart in the middle of a print picks the same video back up instead of starting over.
- Without ffmpeg on the Hub computer no video is made; the card says whether it was found.
