# AssetReady: Discovery

**AssetReady checks a building's handover records, asset by asset, before the FM team accepts the building.**

Prototype with synthetic data. The building (Sarava Tower, Business Bay), the developer, the contractors, the manufacturers and the FM provider (Tessmar Facility Services) are all made up.

## The problem in one paragraph

A building can be construction-complete while the team that will run it is not ready to. Handover transfers more than keys: the FM team needs an accurate asset register, signed commissioning records, valid warranties, O&M manuals and a maintenance plan for every asset. These arrive from many companies, in different formats, and they often disagree: a tag written two ways, a mistyped serial number, a certificate still waiting for its signature, a warranty that started on delivery instead of commissioning. Someone has to open each file, compare fields and chase the contractor, usually against a deadline.

## Evidence

| What | Source | What it shows | What it doesn't |
|---|---|---|---|
| UAE study, 20 interviews (13 FM, 7 construction) | [Property Management, 2025, DOI 10.1108/PM-09-2024-0098](https://doi.org/10.1108/PM-09-2024-0098) ([abstract](https://researchportal.hw.ac.uk/en/publications/collaboration-between-facilities-management-and-construction-sect/)) | A disconnect between FM and construction in the UAE; information transfer, maintainability and defects-liability management can improve | How often handovers are incomplete, or the cost |
| Handover requirements | [PlanRadar handover docs](https://help.planradar.com/en/handovers-overview/) | Certificates, warranties, manuals, outstanding items and formal acceptance are standard handover content | That reconciliation across sources is unsolved |
| Industry commentary | [Kahua](https://resources.kahua.com/blog/ai-for-asset-centric-project-management), [Zutec](https://zutec.com/blog/rethinking-handover-the-biggest-challenges-in-construction-handover) | Handover still often means large volumes of PDFs and spreadsheets | Vendor sources; not independent measurement |

Not established: how much this costs UAE FM providers, how often it happens, or whether anyone would pay for this exact tool. These are validation questions.

## What already exists, and the gap

See [MARKET_SCAN.md](MARKET_SCAN.md). Short version: handover workflow tools, asset-data capture during construction, structured-data (COBie) checkers and CAFM systems all exist.

**Gap (hypothesis):** they assume structured data on a platform the contractor or owner controls. The FM provider that receives the building often gets mixed files from several contractors and has no independent, evidence-backed check before signing. We have not confirmed that no vendor offers this.

## Discovery answers

**User:** FM handover manager at the FM provider taking over the building (primary). Secondary: the developer's asset manager, the project manager, the FM operations manager.

**Who pays (hypothesis):** the FM provider, as part of mobilisation for a new contract; or the developer, to shorten acceptance.

**Workflow:** Pre-acceptance check of every handed-over asset: is the evidence complete, consistent and attributable to this exact unit?

**Trigger:** The contractor issues the handover package, usually two to four weeks before the planned handover date, then sends updates until acceptance.

**Current process:**

```text
1. Receive the contractor's asset register, equipment schedule, certificates, warranties and manuals, often as PDFs and spreadsheets.
2. Import the asset list into the FM team's CAFM system.
3. For each asset, open the documents and compare tag, model, serial, location, signatures and dates.
4. Decide whether differences are harmless or block acceptance.
5. Write to the main contractor for missing or wrong items, track replies, repeat.
6. Sign acceptance, or accept with a list of exceptions.
```

**Pain points:**
- The same asset is described differently in each source.
- Free text (remarks, warranty terms, emails) hides the real status.
- Pressure to accept before evidence arrives ("the certificate will follow").
- Life-safety assets need extra care but are mixed in with everything else.
- Decisions and requests are spread across emails and spreadsheets.

**Agent opportunity:** For each asset, the agent investigates across sources with tools, confirms or rejects possible matches, reads the free text, cites its evidence and drafts the request. Code runs every exact check. A person decides.

**Human boundary:**
- The agent never accepts an asset, sends a message or changes a record.
- It never merges records when the match is uncertain, and never picks between two serial numbers.
- It refuses requests to accept outside the rules, and escalates life-safety assets with open problems.

**Success metric:**
- Prototype: all seeded problems found; status matches the answer key; every quote found in its source; zero acceptances.
- Pilot (later): time per asset to a reviewable decision, share of exceptions found before handover rather than after, contractor turnaround on requests, and no rise in issues found after acceptance.

## Is it a real problem? (plain check)

| Claim | Status |
|---|---|
| Handover records are often incomplete or inconsistent | Partly evidenced (UAE study, industry sources), not measured |
| FM teams check them manually | Plausible, not confirmed by interviews |
| No tool gives the FM side an independent check | Hypothesis |
| An agent is better than rules alone here | Partly shown in the prototype (matching, free text, refusals), not in real use |
