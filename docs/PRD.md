# AssetReady AI: Product requirements

| | |
|---|---|
| Status | Prototype (synthetic data), ready for discovery interviews and a shadow pilot |
| Market | UAE first (Dubai, Abu Dhabi); India second |
| Primary user | FM handover manager at the FM provider taking over a building |
| Secondary users | Developer's asset manager, project manager, FM operations manager |
| Author | Shree Byravi |

## 1. Problem

See [DISCOVERY.md](DISCOVERY.md). FM teams need a reliable way to find and resolve conflicting asset information before operational acceptance, because evidence is spread across many sources and discrepancies need manual investigation.

**Job to be done:** "When I receive a building, help me see which assets have complete, reliable records, which need clarification, and what evidence supports each finding, so I can make an informed acceptance decision."

## 2. Goals and non-goals

**Goals**
- Every asset checked against the same rules before acceptance review.
- Every finding traceable to a quoted source.
- Uncertain matches and pressure to accept are escalated, never decided by the tool.
- Requests to the contractor drafted ready for a person to approve.

**Non-goals (this scope)**
- Formal acceptance or signatures. Defects and snag management. A BIM viewer. A CAFM. Real integrations. Contractor payments.

## 3. Requirements

| # | Requirement | Priority | Status in prototype |
|---|---|---|---|
| R1 | Consolidated view of every asset with rule results | Must | Built (asset register) |
| R2 | Exact checks in code (FM record, commissioning, warranty, O&M, PPM, identity) | Must | Built |
| R3 | Possible tag matches flagged, never auto-linked | Must | Built |
| R4 | Agent investigation with real tool calls, shown step by step | Must | Built (recorded and live) |
| R5 | Every finding cites a source with an exact quote; code verifies quotes | Must | Built |
| R6 | Status recommendation never less strict than the rules; never "accepted" | Must | Built (schema + code guard) |
| R7 | Refuse out-of-policy acceptance requests; escalate | Must | Built |
| R8 | Human approve / edit / reject / escalate, with audit trail | Must | Built (browser storage) |
| R9 | Exception queue across the building | Must | Built |
| R10 | Evaluation against an answer key | Must | Built |
| R11 | PDF and spreadsheet intake | Should | Not built (next scope) |
| R12 | Shared, permanent audit trail and roles | Should | Not built |
| R13 | CAFM export of corrected records | Could | Not built |

## 4. Success metrics

- **North star (pilot):** share of assets reaching a reviewable decision before the handover date, with every exception evidenced.
- **Supporting:** time per asset to a decision; exceptions found before vs after acceptance; contractor turnaround on requests.
- **Guardrails:** zero acceptances by the tool; zero findings without a verifiable quote reaching a person unflagged; no fall in issues caught compared with the manual process.
- **Prototype:** see [EVALS.md](EVALS.md).

## 5. Risks

See [RISK_AND_COMPLIANCE.md](RISK_AND_COMPLIANCE.md).

## 6. Release plan

See [LAUNCH_PLAN.md](LAUNCH_PLAN.md) and [ROADMAP.md](ROADMAP.md).
