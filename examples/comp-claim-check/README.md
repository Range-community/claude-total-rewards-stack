# comp-claim-check: practice data

Paste `claims.md` into Claude and ask: *Check these four pay numbers before we use them.*

## What the skill should find

1. **Claim 1 is unverifiable.** "Saw it online" is not a source: no dataset, no period, no cut. The verdict is Verify at best. The offer is above a number nobody can trace, and a hiring manager acts on it, so the stakes are high.
2. **Claim 2 uses the wrong cut.** The source is named and dated, but it's a UK national, all-industries median used for a London band. The geographic cut doesn't match the role, so the figure needs a London cut before it sets a band.
3. **Claim 3 is a vendor claim with no method.** "90% of the market" and "accurate to within 2%" have no sample, definition or method behind them. The skill should call these uncited, not repeat them as fact.
4. **Decoy: Claim 4 should NOT be flagged as a problem.** It names its source, cut, location, currency and effective date, the cut matches the role, and the stakes are low (an internal check, no pay change). Trust or a light Verify is the right result. If the skill fails this one, it's being too cautious to be useful.
