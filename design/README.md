# AssetReady: Look and feel

- **Mood:** an engineering console for a plant room, not a marketing site. Dark slate background, teal accent for action, status colours that match the readiness rules.
- **Type:** IBM Plex Sans for text, IBM Plex Mono for tags, serials and numbers, so identifiers read exactly.
- **Status colours:** green = ready for review, amber = missing evidence, violet = conflicting information, red = not ready for acceptance, blue = pending contractor clarification.
- **Screens:** Story, Handover overview, Asset register, Investigation (input, context, steps, findings, review), Exception review, Quality checks.
- **Rules for the page:** every finding shows its source; recorded runs are labelled as recorded on screen; the boundary sentence ("Nothing is sent or accepted without a person") sits under every review action; no emoji icons.
- **Tokens** are defined once at the top of `index.html` (`:root`).
