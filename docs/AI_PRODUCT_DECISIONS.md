# AssetReady: AI product decisions

How building an AI agent product differs from a traditional one, the choices made here, and my role.

## What changes when the product is an agent

| Traditional product | AI agent product |
|---|---|
| Same input, same output | Same input can give different answers; you test by running cases many times |
| Requirements describe screens and rules | Requirements also describe judgement: what the agent may decide, and when it must stop |
| QA checks code paths | Evals check behaviour against an answer key, plus stress tests for tricks and failures |
| Errors are bugs | Some errors are judgement calls; you design checks around them, not just fixes |
| Cost is mostly fixed | Each run has a cost and a time; more steps means more cost |

## The main decisions

1. **What is AI and what is code?** Code: tag matching, serials, dates, the six rules, quote checking. AI: deciding whether two differently tagged records are one unit, reading warranty terms and remarks, spotting pressure in an email, writing the request.
2. **How much freedom?** The agent chooses which tools to call and in what order (it's a real investigation), but it can't send, change, link or accept anything.
3. **What does it return?** A fixed schema, so code can check it and the page can show it the same way every time.
4. **How is it kept honest?** Every finding needs an exact quote; code checks it. The status can't be softer than the rules. "Ready" is blocked after a tool failure. Life-safety assets with problems must be "not ready".
5. **What happens when it's unsure?** It says so in `uncertainties`, escalates, and never guesses a serial, a tag or a location.
6. **What about instructions hidden in documents?** They are data. The agent lists what it ignored. Tested in S-01.
7. **How do you test something that varies?** An answer key written before the runs, six eval cases, four stress tests, a person's verdict per case, and a second run after each change. S-02 varied between runs and is kept on record.
8. **When do you change the prompt vs the code?** Prompt for behaviour (S-04: open the documents yourself). Code for anything that must always hold (the life-safety check after S-02 varied).
9. **Which model?** Claude Sonnet: good tool use at a sensible cost per asset. A pilot would compare models on the same answer key.
10. **Why recorded examples?** So the page works for any visitor without an API key. The recordings are real model sessions calling the real tools, labelled as recorded on every screen.
11. **Cost and speed.** About 5 to 10 tool calls and 20 to 40 seconds per asset in the recorded runs. Only assets the rules can't settle need the agent (8 of 24 here).
12. **Where must a person decide?** Every recommendation, every request, and acceptance itself, which stays outside the tool.
13. **What isn't AI's job?** Contract interpretation beyond the stated rules, payment disputes, safety sign-off.
14. **What would make it production-ready?** Real file intake with page references, repeated runs and sampling, permanent audit, roles, and data residency. See [ARCHITECTURE.md](ARCHITECTURE.md).
15. **How would we know it works?** Shadow pilot against the manual process on one real building. See [LAUNCH_PLAN.md](LAUNCH_PLAN.md).

## My role

I framed the problem and the user, scanned the market and chose the narrower angle, wrote the rules, the seeded problems and the answer key, decided what is AI and what is code, set the boundaries, judged the eval results, picked the improvement and wrote the launch plan.
