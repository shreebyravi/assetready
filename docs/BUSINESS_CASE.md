# AssetReady: Break-even model

**This is a model to fill in with real numbers from a pilot, not a forecast.** No figure below is a claim; brackets are inputs to collect.

## Inputs

| Input | Symbol | Value |
|---|---|---|
| Assets per building handover | A | [e.g. 1,500 to 5,000 for a commercial tower] |
| Share of assets the rules can't settle and the agent investigates | s | [prototype: 8 of 24; to measure] |
| Manual review time per investigated asset (hours) | t_m | [to measure in the shadow pilot] |
| Review time per asset with AssetReady (hours) | t_a | [to measure] |
| Loaded cost of a handover engineer per hour (AED) | c | [from the FM provider] |
| Model cost per investigated asset (AED) | m | [recorded runs: 5 to 10 tool calls; price from live runs] |
| Price per handover (AED) | P | [to test] |

## Saving per handover

```text
time saved  = A × s × (t_m − t_a)
money saved = time saved × c − A × s × m
```

## Break-even

The price P is justified when `money saved ≥ P`, before counting harder-to-measure value:

- Problems found before acceptance instead of during the defects-liability period.
- Fewer maintenance gaps from assets missing in the CAFM system.
- A defensible record of why each asset was accepted or held.

## What would make this case fail

- If t_a isn't much lower than t_m because people re-check everything the agent says.
- If incumbent tools already cover the same checks for the client's projects.
- If developers, not FM providers, control the budget and don't see the benefit.
