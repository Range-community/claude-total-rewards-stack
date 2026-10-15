---
name: cycle-planner
description: >-
  Plans a pay review cycle backwards from the date pay has to land, and writes the
  manager guidance pack. You get a dated timeline with an owner for every step (a
  RACI), a list of clashes in your dates, budget or eligibility rules, and a plain
  guidance pack for managers: how to use the matrix, how to talk about the outcome,
  and what not to promise. Use whenever someone asks to plan the merit cycle, build
  the pay review timeline, work back from the payroll cut-off, set the cycle
  calendar, draft the RACI for the cycle, write manager guidance for the pay review,
  prepare the manager briefing, or explain how managers should use the merit matrix.
---

# Cycle Planner

Most pay review cycles go wrong on dates and rules, not on the maths. Approval lands after the payroll cut-off, a briefing is booked on a weekend, two documents disagree on who is eligible, and managers are left to improvise what they can say to their team.

## Before you start: data

You do not need names. Use role titles for owners ("payroll manager"), and employee IDs if you paste any people data. Strip anything not needed for planning: home addresses, health information, bank details. This skill needs dates, rules and totals, not individual pay.

If you are about to paste real personal data into an AI tool your employer has not approved, check that first. If you choose to carry on, that is your call and I will work with what you give me.

To try it first, use the sample inputs in `examples/cycle-planner/`.

## Step 1: Read what you were given

Draft from the inputs straight away. Look for: effective date, payroll cut-off for each country, budget (pool and split by org), eligibility rules, planned dates, and who is named. Ask only about what blocks the plan, such as an effective date or payroll cut-off that is missing. Mark anything missing as "not provided". Never fill a date, deadline or threshold from memory.

## Step 2: Check the inputs against each other

Before building the timeline, test:

- Does final approval land on or before the payroll cut-off, with time for the upload and checks?
- Does any step fall on a weekend or on a date the user has marked as a holiday?
- Do the eligibility rules agree everywhere they appear? Watch "before" against "on or before".
- Does the budget split add up to the approved pool? Show the arithmetic.
- Is every step owned by a named role? A step with no owner is a gap, not a blank to fill.
- Does any country need a consultation or notice step? Do not rule on it. Say "check with counsel or your local HR lead".

## Step 3: Build the timeline backwards

Start at the date pay must land, then work back through: payroll cut-off, upload and checks, approval, calibration, manager proposals, manager briefing, budget sign-off. Leave working days between steps, and say how many you assumed. If the user's draft dates clash, show the draft date, the problem and a proposed date side by side.

## Step 4: Write the manager guidance pack

Only after the user has seen the timeline. Use what they gave you on matrix, guidelines and budget. Keep it to two pages.

## Output template

```
CYCLE PLAN: {cycle name}
Pay lands: {date} · Payroll cut-off: {date per country} · Pool: {% and amount, or "not provided"}

ISSUES TO SETTLE FIRST
1. {issue} | Draft: {date or rule} | Why it fails | Proposed fix
2. ...

TIMELINE (working backwards)
| Step | Date | Responsible | Accountable | Consulted | Informed |
|---|---|---|---|---|---|

MANAGER GUIDANCE PACK (draft, not yet approved)
1. What this cycle is: dates, what managers decide, what they do not.
2. How to use the matrix: rating, position in band, guideline range, where to ask for an exception.
3. How to talk about it: three things to say, in plain words.
4. What not to promise: future increases, promotions, bonus, "next year", anything the guidance does not state.
5. Where to go for help: role title or channel, filled in by you.

OPEN QUESTIONS: {only what is truly blocking}
```

Rules:

- Never invent a market figure, statutory limit, tax rate, threshold or deadline from memory. Dates and budget come from the user or a source they name.
- No tax, legal or regulatory advice. Where law could matter (consultation, notice, works councils), say what to check and with whom. For the EU Pay Transparency Directive, always say "check transposition status and the final rules in your country".
- No vendor names. Say "your HRIS" or "your comp planning tool".
- Show the draft to the user and ask for approval. Nothing goes to managers, employees or a committee until a human signs it off.
- Where an owner is missing, show the gap. Do not invent a person.
- The guidance pack must not promise any outcome or give employees a right to an increase.

## Hand-offs

Run `cycle-upload-checker` once managers have filled the upload. Use `comp-claim-check` on any market figure that appears in the guidance. For the letter employees receive, use `pay-comms-writer`.

## Writing rules

British English unless the user writes American. No em or en dashes: use commas, colons, full stops or brackets. Short plain sentences. No filler. If the user wants a file, make an Excel workbook for the timeline and RACI and a Word document for the guidance pack, using whatever file tools your Claude has.
