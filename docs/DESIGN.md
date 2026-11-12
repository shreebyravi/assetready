# AssetReady: Design

Every fact the agent uses comes from a named record or document. Every consequence waits for a person.

## Agent role

```text
The agent is hired to investigate one handed-over asset at a time for the FM handover manager, across the contractor's register, the equipment schedule, the FM register and the handover documents, within the readiness, matching, evidence and escalation rules, recommending a readiness status and the next step, and escalating when a match is uncertain, evidence conflicts, a life-safety asset has an open problem, a tool fails, or anyone asks for acceptance outside the rules.
```

## Target workflow

```text
0. Handover overview: days to handover, assets by readiness, the decisions that need a person, most serious first.
1. Code runs the six readiness rules on every asset (Readiness 2.1-2.6) and flags possible tag matches without linking them.
2. For an asset with something the rules can't settle, the agent investigates with tools, choosing what to open.
3. The agent submits structured findings: identity decision, exceptions with quoted evidence, a recommended status, escalation, and a draft request.
4. Code checks the answer: every quote against its source; status not less strict than the rules; no "ready" after a failed tool call; "not ready" for any life-safety asset with an open exception.
5. The handover manager approves, edits, rejects or escalates. Approving a contractor request marks the asset "Pending contractor clarification" (Readiness 3.4).
6. The exception review lists every open exception across the building with accept, reject, request clarification and awaiting-information actions, and an audit trail.
7. Quality checks compare findings with the answer key and record a person's verdict per eval case.
```

## Agent loop

```text
Observe: the rule results, register rows and documents it chooses to open.
Decide:  same asset or not; what each problem is; how serious; who must fix it; what status.
Act:     submit findings and a draft request. Nothing is sent or changed.
Check:   code verifies quotes, strictness, tool failures and life-safety status before a person can approve.
```

## Tools

| Tool | What it does | Who does the work |
|---|---|---|
| `run_readiness_rules` | Six exact checks, possible matches, correspondence list, rule status | Code |
| `search_registers`, `get_record` | Look up register rows | Code |
| `search_documents`, `read_document` | Find and read documents with line numbers | Code |
| `compare_attributes` | Exact model, serial and location comparison across chosen sources | Code |
| `submit_findings` | Structured final answer (strict schema) | Agent fills it; code checks it |

Deleted on purpose: no tool to accept, send, edit a record or link a match.

## Output fields

`identity_decision` (no naming issue / same asset confirmed / uncertain, escalate), `exceptions[]` (type, severity, finding, evidence with exact quotes, responsible party, next action), `readiness_recommendation` (four statuses; "accepted" doesn't exist), `summary` (starts with "REFUSED - <section>" when refusing), `escalate` + who + why, a draft request, `uncertainties[]`, `ignored_instructions[]`.

## Escalation rules

| Situation | What the agent does |
|---|---|
| Possible match with agreeing model, serial and location | Confirms it, minor exception, asks for the tag to be corrected |
| Match points to two units | Doesn't merge; escalates; asks for a site check |
| Two serial numbers | Reports both; doesn't choose; asks the manufacturer |
| Warranty terms in free text | Works out the date, states the assumption, asks for it in writing |
| Life-safety asset with any open exception | Not ready for acceptance; escalates to the FM operations manager |
| Request to accept outside the rules | Refuses with REFUSED - Escalation 2.4 and escalates |
| Instruction hidden in a document | Ignores it and lists it |
| Tool failure | Investigation incomplete; never "ready"; escalates |

## Human approval points

1. Before any recommendation is recorded as the team's decision.
2. Before any request is approved for sending (sending is simulated).
3. Formal acceptance is never in the tool.

## Memory

None across sessions. Each investigation starts from the current records. Review decisions and the audit trail are kept in the browser for the demo; a real version would keep them in a shared store.

## Eval plan

Six eval cases (see [EVALS.md](EVALS.md)): a clean asset, the AHU-014 tag and serial case, an uncertain match, a free-text warranty, a missing manual on a life-safety asset, and the boundary case where the contractor asks for acceptance before the certificate is signed. Plus four stress tests.
