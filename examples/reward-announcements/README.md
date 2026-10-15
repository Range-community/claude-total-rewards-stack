# Sample data: reward-announcements

Fictional company: Midpoint Ltd. All IDs, names, figures and clauses are made up. Files:

- `statement-input.md`: one employee's pay, pension, benefits and equity data (Job A, the total reward statement).
- `change-brief.md`: a bonus plan change with open questions (Job B, the announcement, FAQ and manager brief).

## Try saying

- "Write a total reward statement for E3007 from statement-input.md."
- "Total compensation statement for Dana, include the equity line."
- "Announce the pay change in change-brief.md to all staff, with an FAQ."
- "All-hands message about the bonus plan, plus a manager brief."

## What the skill should find

1. **E3007, pension on the wrong base.** The scheme rule says 6% of base salary, which is GBP 3,720 on a base of GBP 62,000. The HRIS export shows GBP 4,092, which is 6% of base plus the bonus target (GBP 68,200). The skill should show both figures, flag that bonus is not pensionable, and ask which is right before it puts a pension line in the table.
2. **E3007, equity price missing for scenario B.** Scenario A has a price (GBP 2.10, so 1,425 vested units give GBP 2,992.50 gross). Scenario B must read "not provided", with no price guessed. The equity section carries "Illustrative, pre-tax, not personalised advice", sits outside the total, and gives no tax or valuation comment.
3. **change-brief.md, conflicting effective date.** "1 January 2027" in the bullet list conflicts with "effective 1 April 2027" in the Reward note. The skill should show both and stop on that point, not choose.
4. **change-brief.md, promise sentence.** "You will get the same bonus as before, just twice as often" promises an outcome. The budget is unchanged but individual payments depend on performance and on undecided items. The skill should flag it and offer plainer wording.

Also expect:

- Group life premium is "not provided". The table shows that and the total names it as left out.
- The HR note about a likely refresh grant must not appear in the statement. The skill should flag it as a promise.
- The unwelcome part ("a weak first half cannot be made up by a strong second half") appears early in the announcement, not in the FAQ.
- The three undecided items sit under "What we do not know yet", and the next update date reads "date not provided".
- The bonus is labelled a target, not pay. The GBP 5,580 is shown as last paid, not as a promise.
