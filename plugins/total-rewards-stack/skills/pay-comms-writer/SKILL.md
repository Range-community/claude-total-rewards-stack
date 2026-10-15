---
name: pay-comms-writer
description: >-
  Writes the individual pay letter from one row of pay review data, in a fixed
  template that says nothing about future pay, and drafts the reply to an
  employee who asks for their pay level and average pay by sex for the same or
  equal value work. You get a checked draft, a list of data problems that stop
  it going out, and a line on what to confirm with counsel. Use whenever
  someone types "write the pay letter", "salary increase letter", "pay review
  outcome letter", "employee asked about their pay level", "pay information
  request" or "Article 7 request".
---

# Pay Comms Writer

A pay letter is the one document every employee reads closely, and it is often the only one kept on file. The usual failures are a wrong number, a letter sent before approval, and a throwaway line that reads as a promise of more next year. A pay information request fails differently: the reply is late, it exposes a small group, or it says more than the law asks.

## Before you start: data

Work from employee IDs and first names only. Leave out home address, bank details, health information and anything else the letter does not need. If you are about to paste real personal data into a tool your employer has not approved, check that first. If you choose to carry on, that is your call and the skill will work with what you give it. To try this first, use the sample data in `examples/pay-comms-writer/`.

## Step 1: Pick the job

Job A is the pay letter. Job B is the reply to a pay information request. If unclear, ask which. Draft from what the user pasted; ask only about what blocks the draft.

## Step 2 (Job A): Check the row before writing

Check each row and list problems at the top of the reply. Do not write a letter for a row that fails a check.

- Approval status is approved. If pending or blank, stop for that row.
- New salary equals current salary plus the stated increase, to rounding. If not, show both figures and ask which is right.
- Currency matches the employee's location and the user's other rows. Flag mismatches.
- A promotion or title change has the new title filled in.
- Manager or HR notes: never copy them. If a note promises or hints at future pay, flag it and leave it out.
- Any field the template needs that is empty: write "not provided" and ask.

## Step 3 (Job A): Write the letter

Use this template exactly. Fill only from the row. No extra paragraphs.

```
Subject: Your pay review outcome, {cycle name}

Dear {first name},

Following the {cycle name} pay review, this letter confirms your outcome.

Current annual salary: {currency} {current}
New annual salary: {currency} {new}
Increase: {pct}%
Effective from: {date}
{Title change: your new job title is {title}.}
{One-off payment: {currency} {amount}, paid with {pay date}.}

This letter confirms your pay from the date above only. It does not set or imply any future pay, bonus or review outcome.

If you have questions, please speak to {contact name or team}.

{Sender name and role}
```

The title change and one-off payment lines appear only if the row has that data.

## Step 2 (Job B): Check the request

Ask for, or confirm the user pasted: the employee's request text, their own pay level, how the category of workers was defined, the average pay level by sex for that category (mean or median, as the user chooses), and the number of people of each sex in the category. Anything missing is "not provided".

- If either sex has fewer than 5 people in the category, do not put that average in the draft. Flag that it may identify individuals and ask the user how their policy handles it.
- Never include a named colleague's pay or anything below category level.
- Never invent an average, a headcount or a deadline.

## Step 3 (Job B): Write the reply

```
Subject: Your pay information request

Dear {first name},

Thank you for your request of {date}.

Your pay level: {currency} {amount} ({basis: annual salary / hourly rate}).
Category of workers: {definition used, in plain words}.
Average pay level in this category: women {amount}, men {amount} ({mean or median}, {date of data}).
{Withheld: we have not shown a figure for {group} because the group is too small to share without identifying individuals.}

If you would like to discuss this, please contact {contact}.

{Sender name and role}
```

Add this line under the draft, outside the letter: "Check with counsel before sending: transposition status and the final rules in your country, the reply deadline, and the required content."

## Rules

- Show the draft and ask for sign-off. A human approves before anything reaches an employee. Never send.
- Never invent a figure, rate, threshold or deadline. Missing means "not provided".
- No tax, legal or regulatory advice. For the EU Pay Transparency Directive, always: check transposition status and the final rules in your country.
- No promises about future pay, ever, in either job.
- Name no comp-tech or benefits vendors. Say "your HRIS" or "your pay review tool".
- One letter per employee. For a batch, produce each letter separately with its own check result.

## Hand-offs

Run `comp-claim-check` on any market figure before it goes into a letter. For the averages behind a Job B reply, `pay-gap-pack` produces them by category of worker. To catch errors across the whole upload before letters are written, use `cycle-upload-checker`.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler such as "We are pleased to". If the user wants files, make Word documents for letters and an Excel log of what was sent, using whatever file tools your Claude has.
