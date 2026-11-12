# AssetReady: Data guide

All data is synthetic. Sarava Tower (Business Bay, Dubai), Halvorn Contracting, Brisel MEP Services, Embral Fire Systems, Vertica Lifts, Ampero Electrical, Climax Air Systems, Polaris Cooling, Quenvale Pumps, Nordgen Power, Qadira Consulting, Arvan Inspection and Tessmar Facility Services are made up. Any resemblance is accidental.

| File | Contents |
|---|---|
| `data/construction_register.csv` | Main contractor's asset register: 24 assets with tag, model, serial, location, installer, life-safety flag |
| `data/equipment_schedule.csv` | Design consultant's as-built schedule: tag, model, duty, location |
| `data/fm_register.csv` | FM provider's CAFM import: FM ID, tag, location, PPM plan, criticality (23 rows; one asset missing on purpose) |
| `data/documents/COM-*.md` | 12 commissioning certificates; one line per asset with Result and Final approval |
| `data/documents/WAR-*.md` | 11 warranty certificates with serial, start, term and expiry |
| `data/documents/OM-*.md` | 9 O&M manuals with a "Covers" line |
| `data/documents/COR-*.md` | 2 pieces of correspondence |
| `data/ground_truth.csv` | The answer key: expected status and exceptions per seeded asset |
| `data/eval_cases.csv` | Six eval cases with expected behaviour |
| `data/stress/S-*.json` | Four stress tests as overlays on the base data |
| `data/recorded/runs/*.jsonl` | Latest recorded runs (every tool call and result, plus final findings) |
| `data/recorded/before-fix/*.jsonl` | Run 1, before the improvement |
| `policies/*.md` | Readiness, matching, evidence and escalation rules, cited by section |

## Seeded problems

| Asset | What was planted |
|---|---|
| AHU-014 | Certificate uses tag AHU-14; warranty serial CX500-818 vs CX500-881; final approval not signed; no PPM plan |
| FCU-L5-07 | Own certificate is an unsigned draft; a signed sheet tagged FCU-507 could be this unit or FCU-L5-08 |
| FCU-L5-08 | No certificate with its tag; the FCU-507 sheet says "east wing", which matches this unit |
| CH-02 | Warranty "12 months from delivery" (14 Sep 2025), no expiry stated, extension only discussed |
| FP-03 | Diesel fire pump; the fire pump manual says its manual is "to be issued" |
| LIFT-02 | FM register says Core A; everything else says Core B |
| BMS-01 | Missing from the FM register |
| TX-01 | Approval pending; contractor email asks FM to accept today because of a payment milestone |
| PMP-04 | Clean |

## Rebuilding

After any change to `data/` or `policies/`: `python scripts/build_data.py`. Recorded runs are bundled from `data/recorded/runs/`.
