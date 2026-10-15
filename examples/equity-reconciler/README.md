# Sample data: equity-reconciler (Midpoint Ltd, fictional)

Try the skill on these files before using your own. Everything is made up. Names are placeholders and emails end in @midpoint.example.

Files:
- `plan_rules_extract.md`: short fictional plan rules (vesting, cliff, leavers, RSU settlement). Paste the clauses you want quoted.
- `grant_register.csv`: 14 grants, as at 30 September 2026.
- `hris_extract.csv`: 14 employees.
- `payroll_extract.csv`: RSU vest lines for the April and July 2026 pay dates.
- `key_dates_entered.csv`: dates a user would type in for the date tracker. Run it with an as-of date of 30 September 2026.

Try: "Reconcile this grant register against the HRIS and payroll extracts. Register as at 30 Sep 2026. Check Q3 2026 vests (1 Jul to 30 Sep)."

## What the skill should find

Reconciliation:
1. **Leaver with active grant.** E1031 (HRIS: terminated 30 Jun 2026, Resignation) still has grant G-0107 as Active, and the register records a 300-share vest on 1 Jul 2026, the day after the Leaving Date. There is no July payroll line for it. Report this ONCE as a leaver problem and mention the missing payroll line inside the same finding. Quote clause 5.3 and 5.2 only if pasted. Do not decide Good or Bad Leaver, or whether the vest stands.
2. **Grant with no HRIS match.** G-0112 belongs to E1099, who is not in the HRIS extract. Payroll paid 125 shares to E1099 on 30 Apr and 31 Jul 2026, so this is also a payroll line for an ID with no employee record. Escalate; do not guess who it is.
3. **RSU vest missing from payroll.** G-0104 (E1017, New York) shows a 200-share vest on 1 Jul 2026 but there is no July payroll line. If clause 6.1 is pasted, quote it (last payroll date of the vest month).
4. **Duplicate grant.** G-0108 and G-0109: same employee (E1038), type, grant date, vesting start and 1,200 shares. Ask the plan admin to confirm whether one is an error. Do not delete or merge anything.

Should NOT be flagged: option grants (G-0103, G-0106, G-0110, G-0114) having no payroll lines, and G-0111 (cliff not yet reached at 30 Sep).

Date tracker (as-of 30 Sep 2026, clauses 4.2 and 4.3 pasted):
- Report A expires on 15 Oct 2026 (entered date plus 12 months entered), 15 days away.
- Report B has no validity period entered: show "not provided" and ask. Never assume 12 months.
- "05/11/2026" is ambiguous (5 Nov or 11 May): ask before placing it.
- G-0111 cliff date is 1 Oct 2026; next quarterly vest dates for the other active grants start 1 Oct 2026. G-0108 and G-0109 cliff on 1 Jan 2027.
- The tracker must not state any valuation or say whether a report is acceptable for any purpose.
