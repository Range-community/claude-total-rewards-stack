---
name: benefits-comms
description: >-
  Builds the open enrolment pack from your plan summary: a timeline email, a
  what-has-changed table, an FAQ and a manager brief. It also sorts incoming
  employee benefits questions into three piles: answer from the policy text you
  pasted, send to the benefits provider, or send to HR because it is sensitive.
  You get drafts for you to approve, never advice on what a plan covers. Use
  whenever someone types "open enrolment pack", "open enrolment email",
  "benefits changes for next year", "benefits FAQ", "manager brief for benefits",
  "triage benefits questions", "employee benefits query" or "who should answer
  this benefits question".
---

# Benefits Comms

Open enrolment fails quietly. An email goes out without the deadline, a change is buried in paragraph six, a manager gets a question they cannot answer and guesses. Then someone chooses cover on a wrong assumption and finds out at claim time. Good comms are short, dated and exact, and they say who to ask.

## Before you start: data

Use the plan summary, not individual records. For Job B, strip names and keep the employee ID or a number. Never paste health details, claim information or medical conditions into a tool your employer has not approved; if an employee has written them in a question, replace them with "[health detail]". If you paste real personal data anyway, that is your decision and your risk. To try this first, use `examples/benefits-comms/`.

## Job A: Open enrolment pack

### Step 1: Read the plan summary

Ask for the plan summary (this year and last year if changes are needed), the enrolment window dates, who to contact, and the portal or form people use. Missing items become "not provided" in the draft; ask for them in one message and do not fill them in.

### Step 2: Write the four pieces

1. **Timeline email**, under 200 words.
2. **What has changed**, a table of only the differences between years.
3. **FAQ**, 6 to 8 questions that the plan summary can answer, with answers quoted or closely paraphrased from it.
4. **Manager brief**, half a page: what changed, what managers can say, what they must send on, and when.

```
Subject: Open enrolment: {dates}

{One line: what employees need to do, and by when.}
Key dates: opens {date}, closes {date}, changes take effect {date}.
What is changing: {2 or 3 bullets, details in the table}
How to enrol: {steps from the user's input}
Questions: {provider or HR contact, per input}
```

```
| Benefit | Last year | This year | What you need to do |
|---|---|---|---|
```

Manager brief headings: What has changed. What you can say. What not to say (no advice on what someone should choose, no medical or personal guidance). Where to send questions. Key dates.

## Job B: Triage employee questions

For each question, classify and give a short draft reply:

- **Answer from policy:** the pasted document answers it. Quote the exact text and say which section. Do not add to it. If the text answers part of the question, answer that part from policy and route only the part it leaves open.
- **Route to provider:** claims, coverage in a specific case, eligibility for a treatment, anything the document is silent on. Draft a handover line and the provider contact if the user gave one.
- **Route to HR:** sensitive or personal matters such as health conditions, pregnancy, mental health, leave, family circumstances, disputes. Reply kindly, share no detail, and name who will call.
- **Route to payroll or tax adviser:** how a benefit is taxed or shows on a payslip.

Output a table: ID, category, reason in one line, draft reply.

## Rules

- A human approves everything before it goes to an employee, manager or committee. Show the draft and ask.
- Never interpret coverage beyond the pasted document. If the text does not say, route it.
- Never invent a date, deadline, contribution rate, limit, premium or eligibility rule. Missing means "not provided".
- No tax, legal or regulatory advice. Say what to check and with whom: your benefits provider, broker, payroll or counsel.
- Do not tell an employee which option to pick.
- Name no benefits or HR system vendors. Say "your benefits provider" and "your HRIS".

## Hand-offs

Use `census-reconciler` to confirm who is actually on the plan before you tell people what they have. Run `comp-claim-check` on any pay or contribution figure quoted in the pack.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler or cheerleading. Write for someone reading on a phone between meetings. If the user wants files, make a Word document for the pack and an Excel file for the triage table, using whatever file tools your Claude has.
