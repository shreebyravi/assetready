# AssetReady: Risk and compliance

## Product risks

| Risk | Impact | Control now | Needed for real use |
|---|---|---|---|
| Agent says an asset is ready when it isn't | Asset accepted with missing evidence | Status can't be softer than rules; "ready" blocked after tool failure; person approves | Repeated runs; sampling; tracking issues found after acceptance |
| Wrong merge of two units | Missing certificate hidden | Code never links; agent must cite agreeing attributes; uncertain matches escalate | Site verification workflow |
| Fabricated or paraphrased evidence | Wrong decisions, lost trust | Code checks every quote word for word | Page and cell references for PDFs and spreadsheets |
| Pressure from the contractor | Premature acceptance | Refusal rule (Escalation 2.4); tool can't accept | Clear policy owner at the FM provider |
| Instructions hidden in documents | Manipulated result | Treated as data; listed when ignored (tested) | Broader injection testing on real files |
| Answers vary between runs | Inconsistent decisions | Code guards for the rules that must always hold | Run each asset more than once; flag disagreement |
| Life-safety assets | Safety exposure | Any open exception means not ready; escalation to operations manager | Alignment with civil defence and authority requirements |
| Tool or document failure | Incomplete investigation | Reported as incomplete; escalated | Retries, alerts |

## Data and privacy

- Prototype: synthetic data only; no personal data; API key stays in the visitor's browser.
- Real use: handover packages are commercial documents and may include names and signatures. Needs a data processing agreement, UAE data residency where the client requires it, no training on client data, access by role, and retention rules.
- UAE Federal Decree-Law No. 45 of 2021 (personal data protection) would apply to any personal data; the DIFC and ADGM free zones have their own regimes. To be confirmed with legal counsel before a pilot.

## What we don't claim

No customer interviews, no adoption, no regulatory approval, no integration, no savings figure.
