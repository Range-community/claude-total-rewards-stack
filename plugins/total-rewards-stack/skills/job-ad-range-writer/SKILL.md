---
name: job-ad-range-writer
description: >-
  Turns a pay band, a role level and a location into the pay range wording for a job ad,
  plus a short script for the moment a candidate asks about pay or is asked what they earn
  now. You get the ad wording, a check that the band is current and in the right currency,
  and a recruiter script that does not rely on pay history. Use whenever someone asks to
  set the range for a job ad, add salary to a job posting, write pay range wording, handle
  pay transparency in an advert, answer "what is the salary" from a candidate, or work out
  what to say about current salary and pay history questions.
---

# Job Ad Range Writer

A range on a job ad is a public promise. Publish one from a stale band, the wrong currency or a number the hiring manager has already said they will exceed, and you either lose candidates or create an equal pay problem you can see in the advert. This skill sets the range from the band, checks the band first, and gives the recruiter something to say when the pay question arrives.

## Before you start: data

You need a band structure, not people. Use role titles and levels, never names. Do not paste candidate details, current salaries or anything personal. If your employer has not approved this tool for pay data, check that first; if you choose to carry on, that is your call and the skill will work with what you give it. To try it first, use `examples/job-ad-range-writer/` (a fictional band file and four ad requests).

## Step 1: Gather what you have

Draft from what the user gave. Ask only for what blocks the range:

- The band row: level, location, currency, min, mid, max, and the date the band took effect
- Whether the ad should show the full band or a narrower hiring range inside it
- Any hiring manager target (so you can test it against the band, not accept it)
- The ad channel and country, for the rules check in Step 4

## Step 2: Check the band before you use it

Run these checks and report each one in a line:

1. A row exists for this exact level and location. If not, say "no band row for this role" and stop. Do not borrow another location's row.
2. The currency matches the location. A Dublin or Amsterdam role in GBP is a data error to fix, not convert.
3. Min, mid and max are in order and mid sits between min and max.
4. The effective date is shown and is within the age the user says is acceptable. If there is no date, or the user has not said what is acceptable, mark the band "not provided" and ask. Do not guess its age.

If the band is stale, undated or unsourced, mark the range Verify and hand the figures to `comp-claim-check` before the ad goes live.

## Step 3: Set the range

- The ad range must sit inside the band. If the hiring manager target is above the band max, say so plainly. That is a band decision for the compensation owner, not a wording fix.
- Offer two options: the full band, or a narrower hiring range inside it with the reason the user gives. Do not choose the narrow range for them.
- Never state what the market pays. If the user wants a market line in the ad, ask for the source and run `comp-claim-check`.

## Step 4: Check the rules, then write

Pay range disclosure rules differ by country, state and city: whether a range is required, what it must cover (base only, or bonus and benefits too), and when it must be shared. List what to check and with whom (your employment counsel or HR adviser). For roles in the EU, check transposition status of the Pay Transparency Directive and the final rules in your country. Do not state a rule from memory.

## Step 5: Output

```
JOB AD RANGE: {role title}, {level}, {location}
Band check: {row found / not found} · {currency ok / mismatch} · {effective date or "not provided"} · {Trust / Verify / Do not ship}
Band: {currency}{min} to {currency}{max} (mid {currency}{mid})

Ad wording (pick one):
A. "Salary: {currency}{min} to {currency}{max} a year, depending on experience."
B. "Hiring range: {currency}{x} to {currency}{y} a year. {What is included: base only / bonus / benefits}."

Flags: {each problem, with the fix and the owner}

Check before publishing: {local disclosure rules, who to ask}

Candidate pay-question script (recruiter):
1. "The range for this role is {range}. Does that work for you?"
2. If asked "why that range?": "It reflects the level of the role and our internal structure."
3. Ask "What are you looking for?" Do not ask "What do you earn now?"
4. If the candidate volunteers their current pay, thank them, do not record it, do not use it to set the offer.
5. If they ask where in the range they would sit: "That depends on the interview outcome and the role scope. I will confirm with the hiring manager."

Approval: Not for publication until {owner} approves.
```

Rules:

- Never invent a market figure, statutory limit, threshold or deadline. Anything year-specific comes from the user or a source they name; otherwise write "not provided" and ask.
- No tax, legal or regulatory advice. Pay history questions are restricted in some places. Say "check local rules with counsel" and default to the script above, which avoids the question.
- Never convert currencies. If the currency is wrong, flag the row.
- Do not promise a position in the range, a bonus or a future rise in the script.
- Show the draft and ask for sign-off. Nothing is published or sent to a candidate or manager by this skill.

## Hand-offs

Run `comp-claim-check` on any stale or market-based figure before the ad goes live. Once an offer is agreed, `pay-comms-writer` handles the letter wording.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler. If the user wants a file, produce Excel for tables and Word for documents with whatever file tools their Claude has.
