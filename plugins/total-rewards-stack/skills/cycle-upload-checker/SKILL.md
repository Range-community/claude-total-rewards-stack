---
name: cycle-upload-checker
description: >-
  Checks a merit upload before it reaches payroll and produces an exceptions log.
  It catches new salaries outside the band, increases above guideline with no
  justification, missing ratings, ineligible people, currency and FTE mismatches,
  and org budgets that are overspent, then gives managers a column to explain each
  exception. Use whenever someone asks to check the merit upload, validate the pay
  review file, find errors in the cycle data, review the comp planning export,
  sanity check increases before payroll, build an exceptions log, justify or log
  off-guideline increases, or find out which orgs are over budget.
---

# Cycle Upload Checker

The merit upload is the last file before pay changes. Errors in it become wrong pay in the next payslip: someone pushed past band maximum, a new joiner with an increase they were never eligible for, a team that spent more than it was given. Finding these takes an hour now or a correction run later.

## Before you start: data

Work from employee IDs, not names. Remove anything the checks do not need: home address, health information, bank details, national ID numbers. The columns that matter are ID, org, country, currency, FTE, hire date, status, rating, band, current and new salary, and any justification.

If you are about to paste real personal data into an AI tool your employer has not approved, check that first. If you choose to carry on, that is your call and I will work with what you give me.

To try it first, use the sample files in `examples/cycle-upload-checker/`.

## Step 1: Get the rules

You need three things from the user. Ask once for any that are missing.

1. Eligibility rule (for example, hire date cut-off and status).
2. Guideline increase by rating.
3. Budget by org, with the currency basis.

Never assume any of them. If a rule is not provided, run the other checks and list the skipped one as "not provided".

## Step 2: Run the checks

Row by row, then by org:

- **Out of band:** new salary above band maximum or below minimum. Check FTE-adjusted bands only if the user says how they work.
- **Above guideline:** increase % over the guideline for that rating. If a justification is written, mark "justified, for approval". If not, mark "missing justification".
- **Missing rating** on anyone who gets an increase.
- **Ineligible:** fails the eligibility rule, or status is not active.
- **Currency or FTE mismatch:** currency does not fit the country, or FTE differs between HRIS and the upload.
- **Budget:** total increase by org against its budget. State the total, the budget and the difference.
- **Arithmetic:** increase % that does not match current and new salary.

Do not flag a row as an error when the data is consistent with the rules. Say how many rows you checked and how many were clean.

## Step 3: Write the exceptions log

Sort by severity: ineligible and out of band first, then missing justification, then budget, then data hygiene. Leave a blank "Manager reason" column and a blank "Decision" column for people to fill in. Do not write the reasons for them.

## Output template

```
UPLOAD CHECK: {cycle} · {n} rows checked · {n} clean · {n} exceptions
Rules used: eligibility {rule or "not provided"} · guideline {source} · budgets {source}

EXCEPTIONS LOG
| # | Employee ID | Org | Issue | Detail (numbers) | Manager reason | Decision |
|---|---|---|---|---|---|---|

ORG BUDGETS
| Org | Budget | Spend | Difference | Status |
|---|---|---|---|---|

ABOVE GUIDELINE, JUSTIFIED (for approval, not errors)
| Employee ID | Increase | Guideline | Justification given |

NOT CHECKED: {rules or columns that were not provided}
```

Rules:

- Never invent a band, guideline, budget, exchange rate, tax rate or threshold from memory. Use only what is in the files or what the user states.
- No tax, legal or regulatory advice. If a country's rules affect an increase (for example, a collective agreement), say "check with payroll or counsel".
- No vendor names. Say "your HRIS" or "your comp planning tool".
- This is a check, not a decision. Show the log and ask the user to approve it. Nothing goes to a manager or into payroll until a human signs it off.
- Do not change the file. Report problems and propose corrections for the user to apply.
- Quote the numbers behind every flag, so the user can verify in seconds.

## Hand-offs

Use `cycle-planner` if dates or eligibility rules are in dispute. Run `comp-claim-check` on any market figure used to justify an exception. When the file is clean and approved, `pay-comms-writer` handles the letters.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler. For files, produce an Excel workbook for the log and budget tables using whatever file tools your Claude has. No custom scripts.
