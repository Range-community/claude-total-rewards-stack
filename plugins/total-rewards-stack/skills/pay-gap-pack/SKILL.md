---
name: pay-gap-pack
description: >-
  Turns anonymised pay data into a pay gap pack by category of worker: mean and
  median gap by category, a flag wherever the gap meets a threshold you set, a
  table of factors that may explain the gap and what is left unexplained, small
  groups suppressed, and then a plain-language explanation of the gap with its
  caveats, drafted for you to review. Use whenever someone asks for a gender pay
  gap by category of worker, a pay gap analysis, a mean and median pay gap, a
  joint pay assessment, an equal pay check by grade, how to explain a pay gap, or
  how to get ahead of a pay gap before employees or a regulator ask.
---

# Pay Gap Pack

A pay gap number with no context gets quoted back at you. A pack that shows the gap, how many people it rests on, what might explain it and what does not is something you can defend. Small groups are the usual trap: a "gap" built on two people identifies them and proves nothing.

## Before you start: data

Use employee IDs, never names. Keep only what the analysis needs: ID, gender, category of worker, pay (annualised full-time equivalent, one currency), location, tenure, and any explanatory factor you want tested. Leave out dates of birth, addresses, health information and bank details.

If you are about to paste real personal data into an AI tool your employer has not approved, check that first. If you choose to carry on, that is your call and I will work with what you give me.

To try it first, use the sample data in `examples/pay-gap-pack/`.

## Step 1: Confirm the set-up

Ask only what blocks the analysis. If the user has not said, ask once:

- What are the categories of worker? They define them (grade, job family, level). You do not.
- What threshold should flag a gap? The user supplies the number. Mention that the EU Pay Transparency Directive uses 5% for a joint pay assessment, and tell them to check transposition status and the final rules in their country. Do not state this as their legal duty.
- Which pay element? Base pay by default. Add others only if the user supplies them.

## Step 2: Calculate

Gap = (men's figure minus women's figure) divided by men's figure. Say so in the pack. Per category, give mean gap, median gap, and n for each group. Then:

- **Suppress any group under 5.** If either group has fewer than 5 people, show the counts and write "suppressed, n<5". No gap, no direction, no conclusion.
- **Flag** a category where the mean or median gap meets or exceeds the user's threshold, in either direction.
- **Mean and median disagree?** Say so, and look for the outlier by ID.
- **Missing or other gender values:** count them, show "not provided", and leave them out of the gap. Do not guess.
- **Pay not on a common basis** (part-time not annualised, mixed currencies): stop and ask.

## Step 3: Factors table

For each flagged category, list the factors the user says matter (tenure, location, performance, scope) and show the data pattern you see. Mark each one "may explain" or "does not appear to explain". Always finish with the unexplained remainder as "not yet explained". Do not call a gap justified or unlawful. That is for counsel.

## Step 4: Plain-language explanation (if asked)

Draft 120 to 180 words for the audience the user names. State the gap, the number of people, what is known, what is not, and what happens next. Include the caveats. Do not promise outcomes.

## Output template

```
PAY GAP PACK: {date} · Pay element: {base} · Threshold: {user's %}
Method: gap = (men minus women) / men · Source: {file}

| Category | n women | n men | Mean gap | Median gap | Flag |
|---|---|---|---|---|---|
| ... | ... | ... | ...% | ...% | Yes / No / Suppressed (n<5) |

Not provided: {count} people with no gender recorded, left out.

FACTORS: {flagged categories only}
| Category | Factor | What the data shows | Status |

NEEDS A HUMAN: {outliers by ID, categories to confirm, data fixes}
EXPLANATION DRAFT: {only if asked}
```

Rules:

- Never invent a market figure, statutory limit, tax rate, threshold or deadline from memory. The threshold comes from the user.
- No tax, legal or regulatory advice. For the EU Pay Transparency Directive, always say "check transposition status and the final rules in your country". Reporting duties belong with counsel.
- No vendor names. Say "your HRIS" or "your payroll export".
- Suppress every group under 5. Never reveal pay for one person.
- A human signs off before anything reaches employees, managers or a committee. Show the draft and ask.

## Hand-offs

Run `comp-claim-check` on any market figure in the explanation. If the question is about who gets promoted, use `promotion-case-checker`. If an employee asks about their own pay, use `pay-comms-writer`.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences, no filler. For files, make an Excel workbook for the tables and a Word document for the explanation using whatever file tools your Claude has.
