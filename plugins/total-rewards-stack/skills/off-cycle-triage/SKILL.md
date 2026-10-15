---
name: off-cycle-triage
description: >-
  Triages a pay increase request made outside the review cycle. It reads the employee's
  pay position against their band, last increase and rating, then gives options (decline,
  hold to the cycle, approve within range) with reasons and knock-on effects on peers and
  pay compression. It can also build a retention case from flight-risk evidence you
  supply. Use whenever someone asks to triage an off-cycle pay request, handle a counter
  offer, justify a mid-year raise, respond to a manager asking for a salary increase
  outside the cycle, build a retention case, or check if an off-cycle raise is fair.
---

# Off-Cycle Triage

Off-cycle raises are where a pay structure quietly breaks. Each one can be defended alone. Together they create compression, anger the peers who waited for the cycle, and teach managers that resigning is the way to get paid. This skill gives each request the same questions, so the answer does not depend on who asked loudest.

## Before you start: data

Use employee IDs, not names. Strip anything not needed: home address, health or leave details, bank details. If your employer has not approved this tool for pay data, check first; if you choose to carry on, the skill will work with what you give it. To try it first, use `examples/off-cycle-triage/` (eight fictional requests with planted problems).

## Step 1: Gather

Draft from what the user gave. For each request you need: employee ID, role and level, location and currency, current salary, the band (min, mid, max, same currency), date and size of the last increase, latest rating, the ask (new salary or percentage), and the manager's reason. For peers, count and median pay in the same role. If a field is missing, write "not provided" and ask only if it changes the answer.

## Step 2: Check the data first

Before any judgement, test the request itself:

- Salary and band in the same currency. A mismatch is a data error. Do not convert.
- Requested salary against band max. Above max is not an off-cycle decision, it is a band or exception decision. Still give the peer, compression and precedent picture, because whoever makes that decision needs it.
- Compa-ratio: salary divided by band midpoint, for current and requested. Show the working.
- Days since last increase and its size. Say the date you are counting from.
- A retention request with no flight-risk evidence is a manager worry, not a case. Say so.
- A market request with no market source: say no source was supplied, ask for it, and hand it to `comp-claim-check`. Never fill the gap with a market figure.

## Step 3: Options

Give all three, then recommend one with the reason. The recommendation is advice. The approver decides.

1. Decline: when the ask is above band, the rating is below expected, or there is no business reason that cannot wait.
2. Hold to the cycle: when the pay position is fine and the next cycle date (user-supplied) is close. State what to say to the manager.
3. Approve within range: when there is a documented reason. Give the size that stays inside the band and the new compa-ratio.

For each option, list knock-on effects: peers now paid less than the person for the same level, how many, and any peer with a higher rating; compression with the level below; precedent for the team.

## Step 4: Retention case (if asked)

Build it only from what the user supplies: evidence of flight risk (a competing offer, a resignation signal, a recruiter approach, with source and date), the person's criticality, and a replacement cost figure. Use the user's replacement figure and say whose it is. Never produce one from memory. If a figure is "not provided", show the case without it.

## Step 5: Output

```
OFF-CYCLE TRIAGE: Request {ID}, Employee {ID}
Data checks: {currency / above max / last increase / evidence}
Position: salary {x}, compa {x.xx} → requested {y}, compa {y.yy}
Last increase: {date}, {size}. Rating: {rating}.

| Option | Reasoning | Knock-on effects |
|---|---|---|
| Decline | | |
| Hold to cycle | | |
| Approve within range | | |

Recommendation: {option and one-line reason}
What to tell the manager: {2 or 3 sentences}
Open items: {what is not provided}
Approval: {approver, as the user names them}. Not communicated to anyone until they sign off.
```

Rules:

- Never invent a market figure, statutory limit, threshold or deadline. Replacement costs, budgets and cycle dates come from the user.
- No tax, legal or regulatory advice. Equal pay exposure from a single raise: say what to check and with whom (counsel, your HR lead). For EU roles, check transposition status of the Pay Transparency Directive and the final rules in your country.
- Never recommend a figure above band max as an off-cycle approval.
- A human approves before anything reaches an employee, manager or committee. Show the draft and ask.

## Hand-offs

Run `comp-claim-check` on any market figure used to justify the ask. If the request is really a promotion, use `promotion-case-checker`. Letters go through `pay-comms-writer`.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler. If the user wants a file, produce Excel for tables and Word for documents with whatever file tools their Claude has.
