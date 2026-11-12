# AssetReady: Architecture

## Now (prototype)

```text
data/*.csv, data/documents/*.md, policies/*.md, data/recorded/runs/*.jsonl
        │  python scripts/build_data.py
        ▼
app/data.js ──► app/engine.js (rules + tools, plain code) ◄── scripts/agent_cli.js (recorded-run harness, Node)
        │                │
        ▼                ▼
index.html + app/app.js (screens, review, audit, live agent loop) ──► Anthropic Messages API (only with the visitor's own key)
```

- **Static page.** No server, no build step for the browser. Works from a double-click or GitHub Pages.
- **One engine, two callers.** `engine.js` runs in the browser and in Node, so recorded runs and live runs use the same rules and tools.
- **Live mode.** The browser calls the Messages API directly with the visitor's key: model `claude-sonnet-5-5`, client tools, `tool_choice: auto`, the final answer through a strict `submit_findings` tool, medium effort, up to 16 turns, with server-side refusal fallback. Errors (bad key, no credit, offline, refusal, cut-off) are shown in plain words.
- **Recorded mode.** Each case was run by a separate Claude Sonnet session whose only allowed command was `scripts/agent_cli.js`. The harness printed the app's own system prompt and tools, executed every tool call with `engine.js`, and wrote each call and result to a JSONL file. The page replays those files.
- **Checks on answers** (`checkFindings`): quotes found in sources; strictness against rule status; life-safety rule; plus, in the page, no "ready" after a failed tool call.
- **State.** Review decisions, verdicts and the API key live in the visitor's browser only.

## Proposed production design

| Layer | Choice | Why |
|---|---|---|
| Intake | PDF/XLSX parsing with page and cell references; COBie import | Real handover packages |
| Store | Postgres: assets, sources, extracted facts with provenance, exceptions, decisions | Audit and multi-user |
| Rules | Same engine as a service, rules configurable per developer and FM contract | Rules differ by client |
| Agent | Server-side tool loop; prompt and tool versions pinned per run; transcripts stored | Reproducible, reviewable |
| Review | Roles (handover manager, operations manager, viewer), SSO | Accountability |
| Output | Request letters, CAFM-ready corrected register, acceptance exception list | Fits existing process |
| Monitoring | Sample of findings reviewed weekly; quote-check failure rate; tool error rate; variance across repeated runs | Answers vary between runs |

Data stays in the client's region (UAE) and is not used for training. See [RISK_AND_COMPLIANCE.md](RISK_AND_COMPLIANCE.md).
