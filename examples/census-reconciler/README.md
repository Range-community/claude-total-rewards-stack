# Sample data: census-reconciler

Fictional company: Midpoint Ltd. All IDs and figures are made up. Both files are as at 30 September 2026 (assume this; the files carry no date).

- `hris-export.csv`: 12 people from the HRIS. Includes an `absence_reason` column.
- `provider-census.csv`: 11 people on the benefits provider's census.

## What the skill should find

1. **E2003, missing from provider.** Active, started 17 August 2026, elected Employee plus dependants, not on the census. The skill should flag it and ask whether a waiting period applies (it must not assume one).
2. **E2009, on provider but left.** Terminated 30 June 2026 in the HRIS, still "active" on the census. Premium is probably being paid for a leaver.
3. **E2006, tier and dependants mismatch.** HRIS says Family with 3 dependants; provider has Employee only with 0. The skill should report both sides and name the owner who must resolve it, without guessing which is right.
4. **Sensitive column for the broker file (Job B).** `absence_reason` (E2007: "Long-term sickness") must be left out of the clean renewal census, and the skill should say it removed it.

All other rows match. Salaries agree everywhere, so any salary flag is a false positive. E2010 and E2012 are clean and should match without comment.
