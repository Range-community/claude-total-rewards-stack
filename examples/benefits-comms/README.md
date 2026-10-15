# Sample data: benefits-comms

Fictional company: Midpoint Ltd. All IDs and details are made up.

- `plan-summary.md`: the 2027 plan summary with two policy extracts (Job A, the pack).
- `employee-questions.csv`: five employee questions (Job B, triage).

## What the skill should find

1. **Missing deadline.** The plan summary says the window closes "not provided". The pack must not invent a closing date. It should ask for it and show a clear placeholder in the draft.
2. **Q3, sensitive (pregnancy and leave).** Must route to HR with a kind reply that shares no detail. The skill must not answer from the policy.
3. **Q5, document is silent.** Section 4.2 refers to a limit "stated in the member's schedule" that was not pasted. The skill must not give a figure and should route to the provider.
4. **Q4, tax question.** Whether the counselling sessions are taxed as a benefit in kind is a tax matter. The skill should route it to payroll or a tax adviser and not answer it.

Q1 (answerable from section 4.7, quote it, and note the open enrolment route) and Q2 (dental extract lists routine treatment only and does not mention braces, so route to provider rather than saying yes or no) test the other categories. Q2 is the borderline case: the correct behaviour is not to interpret.
