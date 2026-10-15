---
name: census-reconciler
description: >-
  Matches your HRIS employee export against the census held by your benefits
  provider, on employee ID, and lists every difference: people missing from the
  provider, people still on the provider who have left, salary or cover tier
  mismatches, dependants that do not agree, and date gaps. You get a
  reconciliation table and an action list by owner. It can also strip the data
  down to a clean renewal census with minimal fields for your broker. Use
  whenever someone types "reconcile the census", "HRIS vs provider", "benefits
  census check", "who is on the policy who has left", "renewal data pack",
  "census for the broker", "clean census" or "membership reconciliation".
---

# Census Reconciler

Insurers bill on the census they hold, not the one you think you sent. A leaver left on the policy costs premium. A joiner missing from it may have no cover when they need it. A renewal quote built on a dirty census is wrong in both directions, and you find out at claim time.

## Before you start: data

Match on employee ID, not names. Drop home address, date of birth (unless the provider requires age bands), bank details, absence reasons and any health information before pasting. Dependant counts are enough; do not paste dependants' names. If you paste real personal data into a tool your employer has not approved, that is your decision and your risk; carry on with what you choose. To try this first, use `examples/census-reconciler/`.

## Step 1: Get both files

You need the HRIS export and the provider census. Ask only for what is missing:

- The columns in each file and what they mean (for example, "cover tier" values)
- The census date (as at which day) for each file
- Whether leavers are removed at the leaving date or at month end, per the user's provider terms

If the two files are as at different dates, say so before comparing; some differences will be timing, not errors.

## Step 2: Match and flag

Match on employee ID. For each ID, check and flag:

- **Missing from provider:** active in HRIS, eligible per the user's rules, not on the census.
- **On provider but left:** on the census, with a leaving date in HRIS before the census date.
- **Salary mismatch:** insured salary differs from HRIS salary. Say the size of the gap and whether the user's cover is salary-linked. Do not assume it is.
- **Cover tier or dependants mismatch:** the HRIS election and the provider tier disagree, or dependant counts differ.
- **Dates:** start date, cover start date or leaving date disagree, or cover starts before employment.
- **Currency or location mismatch,** and duplicate IDs in either file.

Anything the files cannot settle is "unclear, needs checking with {owner}". Never guess which file is right.

## Step 3: Output the reconciliation

```
Census reconciliation: HRIS as at {date} vs provider as at {date}
Matched with no issues: {n} of {n}   Flagged: {n}

| Employee ID | Issue type | HRIS says | Provider says | Likely cause | Owner |
|---|---|---|---|---|---|

Action list
1. {Owner}: {specific action}, {employee IDs}
2. ...

Timing differences (probably not errors): {list or "none"}
```

Owners are roles: HR operations, payroll, benefits provider, broker. Group the action list by owner.

## Job B: Clean renewal census for the broker

When the user wants the renewal file, first run Steps 1 to 3 and resolve or list open flags. Then build a table of minimal fields only: employee ID (or a project ID if the user prefers), location, currency, annual salary, employment status, cover tier, number of dependants, start date. Ask the user to confirm the field list against what the broker actually asked for.

Leave out: names, addresses, dates of birth unless asked for, absence or health fields, bank details, free text notes. Say which columns you removed. Put unresolved flags in a separate cover note, not in the broker file.

## Rules

- Never invent a salary, tier, date or eligibility rule. Missing means "not provided"; ask.
- Do not interpret policy terms (waiting periods, evidence limits, free cover limits). Quote what the user pasted or tell them to ask the provider.
- No tax, legal or regulatory advice. Data protection questions go to your DPO or counsel.
- Name no benefits or HR system vendors. Say "your HRIS" and "your benefits provider".
- Show the table and the action list, and ask the user to approve before anything is sent to the provider or broker. A human sends it.
- Small files only: if the census is too large to check row by row reliably, say so and suggest splitting by country.

## Hand-offs

Run `cycle-upload-checker` first if salaries changed in the last pay review, so the HRIS side is current. For employee-facing messages about cover changes, use `benefits-comms`.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler. If the user wants a file, make an Excel workbook with one tab for the reconciliation, one for actions and one for the broker file, using whatever file tools your Claude has.
