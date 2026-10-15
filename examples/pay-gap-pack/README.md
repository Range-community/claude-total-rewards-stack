# Sample data: pay-gap-pack

Fictional pay data for Midpoint Ltd: 25 people across three user-defined categories of worker. Not real data.

`pay-data.csv` columns: employee ID, gender (F, M or blank), category of worker, location, original currency, FTE, annual base pay as a full-time equivalent in GBP, tenure in years. Currency conversion was done before export at a fixture rate, so no live FX is needed.

Suggested prompt: "Pay gap by category of worker. Flag anything at 5% or more. Mean and median."

Gap is measured as (men minus women) divided by men.

## What the skill should find

1. **Engineering L3 has a real gap:** n=5 women, n=5 men. Mean 66,000 vs 72,000 and median 66,000 vs 72,000, so both gaps are 8.3%, above a 5% threshold. Men also have longer tenure (median 6 vs 3 years), so tenure is a candidate explanation, but the skill must not treat it as one without the user confirming, and must list what is left unexplained.
2. **Operations L2 mean is driven by one outlier:** mean gap 8.7% (46,000 vs 50,400) but median gap 0.0% (46,000 vs 46,000). One man is paid 70,000 against a 44,000 to 48,000 range for everyone else. The skill should flag the mean/median split, name the outlier by employee ID (E3020) and ask whether the role is correctly categorised.
3. **Data L4 must be suppressed:** 1 woman, 3 men. Fewer than 5 in each group, so no gap is reported, even though the raw numbers would give 4.3%.
4. **One person has no gender recorded:** E3021 in Operations L2 is excluded from the gap and shown as "not provided" (1 person), not guessed.

## What the skill should NOT do

- Report a gap for Data L4.
- Say the Engineering gap is "explained by tenure" or call it lawful or unlawful.
- Quote any legal threshold as fact. The 5% figure is the user's; the skill may say the EU Pay Transparency Directive uses 5% for a joint pay assessment and must tell the user to check transposition status and the final rules in their country.
