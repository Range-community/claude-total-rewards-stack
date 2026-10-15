# Sample data: equity-explainer (Midpoint Ltd, fictional)

Everything is made up. Paste `plan_rules_extract.md` plus the grant you want explained, then ask the questions in `employee_questions.md` or the cases in `leaver_cases.md`.

Try: "Explain vesting for Grant A to the employee, with scenarios at USD 4.00 and USD 6.00. Plan clauses and grant terms are pasted."

## What the skill should find

Tile A, vesting explainer:
1. **Grant A schedule from clauses 4.1 to 4.3.** Cliff 1 July 2025 (800 units), then 12 quarterly instalments of 200 units (6.25% of 3,200) from 1 October 2025 to 1 July 2028. At 30 September 2026, 1,600 units have vested (800 plus 4 instalments), next vest 1 October 2026. Scenario values are units times the price the user gave, and every scenario output carries the label "Illustrative, pre-tax, not personalised advice."
2. **Acceleration question (Q2).** Clause 4.4 says no acceleration unless the Award Letter expressly provides, and Grant A's letter says nothing. The skill quotes clause 4.4 and the letter, says the pasted terms contain no acceleration, and sends the employee to the plan administrator. It must not say "you will be accelerated" or "you will lose them".
3. **Document conflict on Grant B (Q4).** The award letter says first vest at 6 months, clause 4.2 says the Cliff Date is the first anniversary. The skill shows both quotes side by side, does not pick a winner, and asks the plan administrator or counsel which governs. It can show the schedule under clause 4.2 as "per the clause pasted" and mark it unconfirmed.
4. **Refusals.** Q3 (tax), Q5 (future worth) and Q6 (should I exercise early) are declined in one plain line each, with who to ask (tax adviser; nothing to predict; independent adviser). No tax rates, no price forecast, no recommendation.

Tile B, leaver checklist:
5. **Case 1.** HRIS says Resignation but the manager note says mutual agreement: category is unclear. The skill must not label the employee Good or Bad Leaver. It quotes clauses 5.1, 5.2, 5.5 and says the Committee, plan administrator and counsel confirm. It notes the exercise window (clause 5.4, 6 months) applies only if Good Leaver, and that vested Options lapse on the Leaving Date if Bad Leaver (clause 5.5) unless the Committee decides otherwise in writing. The 1 October 2026 vest falls before the 31 October Leaving Date and the 1 January 2027 vest after it: show both and quote clause 5.3 for the later one.
6. **Case 2, boundary dates.** The 1 October 2026 vest falls before the Leaving Date of 31 October 2026 (vests while employed per the dates given). The 1 January 2027 vest is after the Leaving Date, so clause 5.3 is the clause to quote and confirm. No Committee decision is pasted: list it as an open item, not as a lapse.
