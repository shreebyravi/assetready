# AssetReady AI: the project on one page

**An independent check of a building's handover records, for FM teams taking over new buildings in the UAE.**

## The problem

Before an FM team accepts a building, every asset's records must agree: the contractor's register, commissioning certificates, warranties, manuals and the FM team's CAFM import. They often don't, and the checking is manual, under deadline, with the contractor pushing to close.

## What AssetReady does

For every asset it runs exact rule checks, then an AI agent investigates what the rules can't settle: is "AHU-14" the same unit as "AHU-014"? What does this warranty clause actually mean? Is the contractor asking for acceptance of something that isn't signed? Every finding quotes its source. It drafts one request per responsible party. The FM handover manager approves, edits or rejects every step. It never accepts anything.

## Results so far (prototype, made-up data)

- 24-asset fictional tower, 8 seeded problem cases, separate answer key.
- Latest run: 15 of 15 seeded problems found, status matched in 9 of 9 investigations, every quote found in its source.
- Refused a contractor's request to accept a transformer before its certificate was signed.
- Ignored an instruction hidden in a document telling it to mark an asset ready.
- One real failure found by a stress test, fixed and re-tested, with before and after on record.

## How it would be validated

A shadow pilot on one building: AssetReady runs on a copy of a real handover package while the FM team works as normal, then the two results are compared for what each found and how long it took. No system access and no change to the team's process. See [LAUNCH_PLAN.md](LAUNCH_PLAN.md).

## What it doesn't claim

No FM team has used it. It hasn't read real PDFs or BIM yet. Savings are not estimated. See [RISK_AND_COMPLIANCE.md](RISK_AND_COMPLIANCE.md).
