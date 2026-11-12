# AssetReady: Case study

## The question

Why can a building be construction-complete while the FM team still isn't ready to run it?

## What I did

1. **Framed the problem** from a 2025 UAE study and public handover practice, and wrote down what the evidence doesn't show (frequency, cost, willingness to pay).
2. **Checked the market.** PlanRadar, Zutec, Procore, Autodesk, Zepth and COBie checkers already cover a lot. A generic "AI handover assistant" would overlap. I narrowed it to an independent check for the FM provider on the mixed files it actually receives.
3. **Chose the user:** the FM provider's handover manager, because the FM side carries the risk after acceptance and doesn't control the contractor's tools.
4. **Split the work:** code for every exact check; the agent for judgement (is AHU-14 the same unit as AHU-014? what does this warranty clause mean? is this email pressure?); a person for every decision.
5. **Built a fictional tower** with 24 assets, 34 documents and 8 seeded problems, and wrote the answer key before any run.
6. **Ran real model sessions** (Claude Sonnet) that called the app's own tools, with every call logged by code.
7. **Tested it:** six eval cases, four stress tests, and checks in code on every answer.

## What went wrong, and what changed

- **Run 1, S-04:** the agent trusted the rules' "pass" and never opened the warranty, so it missed that the document couldn't be read. I changed one instruction (open the certificate and warranty yourself before saying ready) and added a code check (no "ready" after a failed tool call). Run 2 behaved correctly.
- **Run 2, S-02:** for a lift with a contradictory Arabic remark, the agent found the problem but chose a softer status than the rules require. In run 1 it chose correctly. Rather than tune the prompt until one run looked right, I added a code check: any life-safety asset with an open exception must be "not ready". That's the lesson: prompts shape behaviour; code enforces what must always hold.
- **Names:** two fictional company names resembled real firms, so I renamed them.

## Results (prototype)

15 of 15 seeded problems found, status matched in 9 of 9 investigations, every quote found in its source, refusal held, hidden instruction ignored. My verdicts: 5 Pass, 1 Needs work (a clean result has no field for its evidence).

## What I'd do next

Interview FM handover managers, trial two incumbents on the same package, then run a shadow pilot on one real building. See [LAUNCH_PLAN.md](LAUNCH_PLAN.md).
