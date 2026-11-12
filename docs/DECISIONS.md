# AssetReady: Decisions

| # | Decision | Why | Trade-off |
|---|---|---|---|
| 1 | Primary user is the FM provider's handover manager | The most independent position: the FM provider carries the risk after acceptance and doesn't control the contractor's platform | Developers may be the easier buyer; kept as a secondary user |
| 2 | Position as an independent pre-acceptance check, not a handover platform | PlanRadar, Zutec, Procore, Autodesk and Zepth already collect handover data | Narrower market; must prove value on messy inputs |
| 3 | Dubai commercial office tower as the demo | Densest technical handovers and the largest FM employers; transfers to Indian commercial parks | Residential handovers have different stakeholders |
| 4 | Code does every exact check; the agent only judges | Exact things must be repeatable and testable | More code to maintain |
| 5 | Code flags possible tag matches but never links them | A wrong merge hides a missing certificate | The agent must do more work per asset |
| 6 | The agent cannot accept: "accepted" isn't in its output options | Acceptance carries contractual weight | Every asset still needs a person's sign-off |
| 7 | Final answer through a strict schema tool | Predictable fields the page and the checks can rely on | Less freedom in how the agent writes |
| 8 | Code checks every quote against its source | Fabricated citations are the main risk with reading tasks | Paraphrased but correct quotes get flagged |
| 9 | Status may never be less strict than the rules | The rules are the floor; the agent can only add judgement | Agent can't overrule a wrong rule result without a person |
| 10 | Life-safety assets with any open exception are "not ready" | Fire systems, lifts and standby power can't be accepted on partial evidence | Some minor items will block more assets |
| 11 | Recorded answers by separate Claude Sonnet sessions calling the real tools | Works for visitors without an API key; still a real model choosing real tool calls | Can't be re-run by visitors without a key; one run per case |
| 12 | One improvement driven by a stress test (S-04), with before and after kept | Shows the evaluation loop honestly | The fix adds a few tool calls per asset |
| 13 | Keep a run that varied (S-02) on record, and add a code check | Answers vary; the check is the real control | The quality page shows a "not as expected" row |
| 14 | Static page, same engine in browser and Node | Free hosting, double-click to run, same code for recorded and live | No shared state between users |
| 15 | Requests are drafted, never sent | Messages to contractors have commercial consequences | A person copies the draft into email |
