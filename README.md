# AssetReady AI

**A building can be finished and still not be ready to run. AssetReady checks every asset's handover records before your FM team accepts the building.**

An AI agent prototype for facilities management teams taking over a new building. It matches records that use different tags, finds what is missing or contradictory, quotes the evidence, and drafts what to ask the contractor. A person decides everything.

**[Try it, no login needed](https://shreebyravi.github.io/assetready/)** | **[The project on one page](docs/PITCH.md)** | **Status:** prototype with made-up data

[![Watch the 2-minute AssetReady walkthrough](video/poster.jpg)](https://shreebyravi.github.io/assetready/video/assetready-walkthrough.mp4)

**[Watch the 2-minute walkthrough](https://shreebyravi.github.io/assetready/video/assetready-walkthrough.mp4)** (AI voice)

![Handover overview](docs/images/overview.jpg)

## The problem

At handover, the FM team receives records about the same equipment from many companies: the main contractor's asset register, the design consultant's equipment schedule, commissioning certificates, manufacturers' warranties, O&M manuals and an import sheet for its own CAFM system. They often disagree. One tag is written two ways, a serial number is mistyped, a certificate is still waiting for its signature, and a warranty started on the wrong date.

A 2025 peer-reviewed study of the UAE ([Property Management, DOI 10.1108/PM-09-2024-0098](https://doi.org/10.1108/PM-09-2024-0098)), based on 20 interviews with FM and construction professionals, found a disconnect between the two sectors and pointed to better information transfer as an area to improve. It does not say how often handovers are incomplete or what that costs. Those questions are still open.

Handover platforms (PlanRadar, Zutec, Procore, Autodesk, Zepth) and COBie data checkers already exist. **Our hypothesis** is that the FM provider receiving the building has no independent check of the mixed files it is actually handed. AssetReady is that check. See the [market scan](docs/MARKET_SCAN.md).

## What it does

| Step | What happens | Who decides |
|---|---|---|
| **Check** | Plain code runs six rules on every asset: FM record, signed commissioning, valid warranty, manual, maintenance plan, matching identity | Automatic |
| **Match** | Code flags "AHU-14" as a possible match for "AHU-014" but never links it; the agent confirms only when model, serial and location agree | Agent, with rules |
| **Investigate** | The agent chooses which records and documents to open, reads remarks, warranty terms and contractor emails, and quotes what it relies on | Agent, with tools |
| **Recommend** | It recommends a readiness status, who must fix what, and drafts the request | Agent proposes |
| **Decide** | The handover manager approves, edits, rejects or escalates; requests are drafted, never sent; acceptance is signed outside the tool | A person |

![An investigation, step by step](docs/images/investigation.jpg)

## Why it can be trusted with this job

- **Code handles what must be exact:** tag matching, serial comparison, dates, the readiness rules.
- **AI handles what needs reading and judgement:** confirming a possible match, reading free-text warranty terms, remarks and contractor emails.
- **People decide what has consequences:** every recommendation and every request.
- **It cannot accept anything.** "Accepted" isn't one of its options.
- **Limits are enforced twice.** Code checks every quote against its source, blocks any answer less strict than the rules, blocks "ready" when a tool failed, and blocks anything but "not ready" for a life-safety asset with an open problem. In one run of a stress test the agent chose a softer status for a lift; code blocked approval of that answer.

![The agent refuses pressure to accept](docs/images/refusal.jpg)

## How it was tested

- **One fictional tower with 24 assets**, 34 short documents and 8 seeded problem cases, with a separate answer key ([data/ground_truth.csv](data/ground_truth.csv)).
- **Six eval cases** with expected results written first. In the latest run, all 15 seeded problems were found, the status matched the answer key in all 9 investigations, and every quote was found in its source. My verdicts: 5 Pass, 1 Needs work.
- **Four stress tests:** a hidden instruction in a document, a remark in Arabic that contradicts a field, a duplicate FM record, and a document that can't be read.
- **One documented improvement:** in run 1 the agent trusted the rules without opening the warranty, so it missed that the document couldn't be read. One instruction fixed it in run 2.

The answers shown are recorded examples: real Claude Sonnet sessions that called this app's own tools, with every call logged by code. A visitor can add their own Anthropic API key to run it live. Details are in [docs/EVALS.md](docs/EVALS.md).

![Quality checks](docs/images/quality.jpg)

## Known limits

- No FM team has used it, and all building data is made up.
- It reads short text documents, not real PDFs, scans, drawings or BIM models.
- It checks one asset at a time, not whole systems, defects or snag lists.
- The readiness rules are a simplified, fictional set.
- The product gap is a hypothesis. See the [market scan](docs/MARKET_SCAN.md).

## What's next

1. **Validate:** talk to FM handover managers in Dubai and Abu Dhabi, and trial the incumbent tools.
2. **Pilot on one building:** shadow mode first, on a real handover's documents. See the [launch plan](docs/LAUNCH_PLAN.md).
3. **Read real files:** PDF and spreadsheet intake, COBie import, a CAFM export. See the [roadmap](docs/ROADMAP.md).

**Author:** Shree Byravi · [LinkedIn](https://www.linkedin.com/in/shree-byravi/)

## AI product decisions

What should AI do and what should code do? How much freedom does the agent get? How do you test answers that vary? See [AI product decisions](docs/AI_PRODUCT_DECISIONS.md), the [case study](docs/CASE_STUDY.md), the [break-even model](docs/BUSINESS_CASE.md) and the [backlog](docs/BACKLOG.md).

## What's in this repo

| Path | Contents |
|---|---|
| `index.html` | The page |
| `app/` | `engine.js` (rules and tools), `app.js` (screens and live agent loop), `data.js` (generated bundle) |
| [`docs/`](docs/README.md) | PRD, architecture, decisions, risks, evals, launch plan and more |
| `data/` | Made-up registers, documents, answer key, stress tests and recorded runs |
| `policies/` | The fictional rules the agent follows |
| `scripts/` | `build_data.py` (bundles data) and `agent_cli.js` (the recorded-run harness) |
| `design/` | Notes on the look and feel |
| `video/` | The walkthrough video |

## Run it yourself

Open `index.html` in Chrome or Edge. It runs on recorded answers. To run it live, add your own Anthropic API key in Settings; the key is saved only in your browser. After changing anything in `data/` or `policies/`, run `python scripts/build_data.py`.

## Data, privacy and licence

All data is synthetic. The building, developer, contractors, manufacturers and FM company are made up, and any resemblance is accidental. Product names in the market scan are real companies, named only to compare. No keys or personal data are stored here.

**Created by Shree Byravi.** See also [SpaceBack](https://github.com/shreebyravi/spaceback) and [ScreenGate](https://github.com/shreebyravi/screengate).

Licensed under [CC BY-NC-ND 4.0](LICENSE).
