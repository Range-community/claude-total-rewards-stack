# Sample data: cycle-planner

Fictional cycle inputs for Midpoint Ltd. Use `cycle-inputs.md` as the starting message.

## What the skill should find

1. **Approval after payroll cut-off:** executive committee approval is Wednesday 16 December 2026, but the payroll cut-off is Friday 11 December (US: 14 December). Approved pay cannot reach January payroll.
2. **Manager briefing on a Saturday:** 14 November 2026 is a Saturday. It needs a working day, before proposals open.
3. **Eligibility rule conflict:** the policy doc says joined before 1 July 2026, the HRBP FAQ says on or before 1 October 2026. The skill must ask which one is right, not pick one. Note also "before" and "on or before" differ on the boundary day.
4. **Budget split adds up to more than the pool:** the proposed org percentages total 370,000 (3.7% of payroll) against an approved pool of 350,000 (3.5%). Engineering at 4.0% is 20,000 over its share; the split is over by 20,000 in total.

Also expect: no owner named for the HRIS upload step (the RACI should show a gap, not invent a name), and a prompt to check local consultation requirements with counsel for Ireland and the Netherlands rather than a ruling.
