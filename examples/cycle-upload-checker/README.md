# Sample data: cycle-upload-checker

Fictional merit upload for Midpoint Ltd (17 people, GBP, EUR and USD). Not real data.

Files:

- `merit-upload.csv`: the upload export. One row per person, with current and new salary, band, rating, guideline and any manager justification.
- `org-budgets.csv`: the merit budget per org, in GBP equivalent.

Cycle rules to paste alongside the files:

- Eligible: active, hired on or before 1 July 2026.
- Guideline maximum by rating: Exceeds 6.0%, Strong 4.5%, Meets 3.0%, Below 0.0%.
- Anything above guideline needs a written justification.
- `increase_gbp_equiv` uses fixture rates (EUR 0.86, USD 0.78). They are made up for this test, not market rates.

## What the skill should find

1. **E1007 (Engineering, UK):** new salary 100,700 is above the band maximum of 98,000. Out of band after the increase.
2. **E1011 (Operations, UK):** 8.9% increase on a Meets rating (guideline 3.0%) with no justification.
3. **E1019 (Operations, UK):** hired 14 September 2026, after the 1 July cut-off, but has an increase. Ineligible person included.
4. **Sales org:** increases total 11,124 against a budget of 10,000, so 1,124 over. Engineering (19,360 of 20,000) and Operations (11,624 of 12,000) are inside budget.

## What the skill should NOT flag

- **E1014:** 6.8% on an Exceeds rating is above the 6.0% guideline, but a justification is written. Log it as "above guideline, justified", for approval, not as an error.
- FTE matches between HRIS and upload on every row. Currency matches country on every row.
- No ratings are missing.
