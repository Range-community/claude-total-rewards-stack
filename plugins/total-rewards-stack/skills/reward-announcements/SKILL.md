---
name: reward-announcements
description: >-
  Writes two things. A total reward statement for one employee: a plain-English
  one-page narrative and a simple table of base pay, bonus, employer pension and
  employer-paid benefits, plus equity only if you supply grant terms and a price.
  Or a leadership announcement of a pay or policy change, with an FAQ, a
  what-we-know block and a manager brief. You get a checked draft, data gaps and
  any sentence that reads as a promise. Use whenever someone types "total reward
  statement", "total compensation statement", "announce the pay change", "announce
  the pay freeze", "all-hands message about the bonus plan", "FAQ for the new bands"
  or "manager brief for the pay change".
---

# Reward Announcements

A total reward statement fails when it adds up numbers nobody checked and quietly promises a bonus. A change announcement fails when the bad news sits in paragraph five and one cheerful sentence ("nothing changes for you") turns out to be untrue. Both go to many readers and cannot be taken back.

## Before you start: data

Work from employee IDs and first names only. Leave out home address, bank details, health information and anything else the document does not need. If you are about to paste real personal data into a tool your employer has not approved, check that first. If you choose to carry on, that is your call and the skill will work with what you give it. To try this first, use the sample data in `examples/reward-announcements/`.

## Step 1: Pick the job

Job A is the total reward statement for one person. Job B is the announcement of a pay, bonus or reward policy change to many people. An open enrolment pack or a change to benefit plans goes to `benefits-comms`. If unclear, ask which. Draft from what the user pasted; ask only about what blocks the draft.

## Job A: Total reward statement

### Step 2A: Check the data before writing

List problems at the top of the reply. Do not write a line you cannot support.

- Use only figures the user supplied. Employer-paid benefit values come from the user's provider documents. If a value is missing, write "not provided" and ask.
- Recalculate any percentage against the base the user's own policy text names (for example base salary, or total earnings). If a stated amount does not match, show both figures and ask which is right. Until the user answers, that table line reads "to confirm" and stays out of the total.
- Currency and period (annual, monthly) are stated and consistent. Flag mismatches.
- Bonus: say whether the figure is a target or an amount paid. A target is never written as pay.
- Equity: include it only if the user supplied the grant terms (the pasted clause), the vested and unvested units, and a price. A missing price for a scenario is "not provided". Do not fill it in.
- Never give tax treatment of any item. If asked, say who to ask: your payroll team or a tax adviser.

### Step 3A: Write the statement

```
Subject: Your total reward statement, {date}

Dear {first name},

{Narrative, about 150 words, plain English. Say what you are paid, what the
company puts in on top, and what the benefits are worth to the company. Say the
bonus is a target and not a promise.}

| Item | Annual amount ({currency}) | Note |
|---|---|---|
| Base salary | {amount} | {as at date} |
| Bonus target | {amount} | {target, not guaranteed} |
| Employer pension | {amount} | {rate and the base it applies to} |
| {Each benefit} | {amount or "not provided"} | {source document} |
| Total shown | {sum of lines with a figure} | {name any "not provided" lines left out} |

{Equity section only if the user supplied everything. One row per price the
user gave: price used, vested units, gross figure. Never add it to the total.
Then: "Illustrative, pre-tax, not personalised advice."}

This statement shows your package as at the date above. It does not set or imply any future pay, bonus or review outcome. Figures are annual.

If you have questions, please speak to {contact}.

{Sender name and role}
```

## Job B: Announcement of a change

### Step 2B: Check the brief before writing

Ask for: what is changing, from when, who is affected and who is not, what stays the same, budget impact (only if the user supplied it), decisions still open, who to contact, and when the next update is. Then check:

- Every date agrees across the whole brief. If two lines conflict, show both and stop on that point.
- Open questions are never written as decided.
- Flag every sentence that sounds like a promise ("you will", "no one will be worse off", "the same as before", "guaranteed", "always"). Show the sentence and a plainer version. A promise is acceptable only if the user confirms it is decided and binding.
- Name the unwelcome part early. If the brief hides it, say so and move it up.
- Whether the change needs consultation, notice or agreement is a question for counsel. Say so; do not answer it.

### Step 3B: Write the announcement

```
Subject: {What is changing}, from {date}

{Two sentences: what is changing, who it affects, from when.}

The part you may not like: {the unwelcome bit, stated plainly, in this paragraph}.

What this does not change: {bullets, only things the user confirmed}

What we know: {bullets}
What we do not know yet: {bullets, one per open question}
When you will hear more: {date and channel, or "date not provided"}

Questions: {contact}
```

Then add, outside the message:

- **FAQ:** 6 to 8 questions that the brief can answer, plus "What happens if my situation does not fit?" routed to HR. No answer goes beyond the brief.
- **Manager brief,** half a page: what changed, what you can say, what not to say (no individual predictions, no hints about anyone's pay), where to send questions, and key dates.

## Rules

- Show the draft and ask for sign-off. A human approves before anything reaches an employee, manager or committee. Never send.
- Never invent a figure, rate, threshold, date or deadline. Missing means "not provided".
- No promises about future pay, bonus or review outcomes, and no "you will receive" about anything not confirmed.
- No tax, legal or regulatory advice. For the EU Pay Transparency Directive, always: check transposition status and the final rules in your country.
- Equity refusal list: no tax rates or tax treatment of ISO, NSO, EMI, RSU or 83(b) questions; no valuations or share price predictions; no interpretation of plan rules beyond quoting the clause the user pasted. Decline in one line and name who to ask: your tax adviser, plan administrator or counsel. Every equity figure carries: "Illustrative, pre-tax, not personalised advice."
- Name no comp-tech or benefits vendors. Say "your equity platform export", "your HRIS", "your benefits provider".
- One statement per employee. For a batch, produce each separately with its own check result.

## Hand-offs

Individual pay letters and pay information requests belong to `pay-comms-writer`. Open enrolment packs and benefits questions belong to `benefits-comms`. For a fuller equity explanation, use `equity-explainer`. For manager guidance on a pay review cycle, use `cycle-planner`. Run `comp-claim-check` on any market figure before it goes in a statement or announcement.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler such as "We are pleased to" and no spin. Write for someone reading on a phone between meetings. If the user wants files, make a Word document for the statement or announcement and an Excel file for the table, using whatever file tools your Claude has.
