---
name: committee-deck-builder
description: >-
  Turns a pay decision into the storyline for a reward committee or executive team, and a
  one-page board summary. You get a slide-by-slide outline (sentence titles, the message,
  what goes on each slide, what the speaker says), the numbers checked against each other,
  the hardest question with an honest drafted answer, and what you do not know. Use
  whenever someone asks to predict the hardest question the committee will ask,
  build the committee deck, write a board paper for the pay review, draft an exec summary for
  the pay decision, structure a reward committee presentation, prepare the remuneration
  committee pack, or write a one-page summary of a pay proposal.
---

# Committee Deck Builder

Pay proposals rarely fail on the idea. They fail because the ask is on slide nine, the cost does not match the headcount, and the first hard question has no prepared answer. This skill builds the storyline so the committee knows what you want in the first thirty seconds, and so you have checked your own numbers before they do.

## Before you start: data

Use totals, bands and counts, not names. Strip anything not needed: individual salaries, health or leave details, bank details. If your employer has not approved this tool for pay data, check first; if you choose to carry on, the skill will work with what you give it. To try it first, use `examples/committee-deck-builder/` (a fictional brief with planted problems).

## Step 1: Gather

Draft from what the user gave. Look for: the decision requested, who it covers (headcount), current and proposed pay position (band, midpoint, average increase), total annual cost, the budget available, the evidence (attrition, vacancies, time to hire, exit reasons), the alternatives already considered, the decision date and the effective date. Write "not provided" for anything missing. Ask only for what blocks the ask: the decision, the cost, the date.

## Step 2: Check the numbers first

Before any slide, test the brief:

- Headcount times average increase against the stated total cost. Show the working. If they differ, do not pick one. Ask what the gap is (on-costs, phasing, a different headcount) and say so on the slide.
- Total cost against budget available, for every cost figure: subtract, then name the result from the sign. Cost above budget is "over budget by", cost below is "headroom of". In the user's currency.
- Every rate compared over the same period and the same population. A 12-month rate set beside a part-year or annualised rate is not like for like. Show both, with the counts behind them.
- Any market claim ("below market", "at the 40th percentile") without a named source. Mark it "unsourced", leave it off the slide, and run `comp-claim-check` first.
- A decision date. No date means the slide cannot say "by when". List it under NEEDS A HUMAN.

## Step 3: Build the storyline

Answer first. Slide 1 states the decision requested and the cost. Every slide title is a sentence that states its finding, not a topic ("Engineering attrition has doubled" not "Attrition"). Default order, cut what the decision does not need:

1. The ask: the decision, the cost, the date.
2. Why now: the problem, in the user's evidence.
3. What the evidence shows: attrition, vacancies, exit reasons, as supplied.
4. What we propose: who is covered, how, effective date.
5. What it costs: total, per head, against budget, phasing.
6. The risks: of acting, and of not acting.
7. The alternatives: each with cost and what it leaves unsolved.
8. The hardest question, and what we do not know.
9. The decision needed and by when, and what happens next if yes.

Appendix: sources and assumptions, one line per figure. For any chart, hand the data to `pay-data-charts` by name and say what the chart should show; do not draw it here.

## Step 4: The hardest question

Pick the question a sharp committee member would ask first, usually cost against budget, why these people and not others, or what stops the next team asking. Draft an honest answer from the user's material only. If the honest answer is "we do not know", say that, and say how and by when you would find out. Then list what we do not know: every missing figure, every assumption, every claim without a source.

## Step 5: Board summary

One page, under 250 words, plain sentences, no jargon. Count the words. Five headings: the decision, the number, the why, the risk, the ask. Use only checked figures. If a figure is "not provided", say so in the text.

## Output template

```
COMMITTEE STORYLINE: {proposal}   Decision date: {date or "not provided"}
NUMBERS CHECK: {each test, the working, the result}

SLIDE {n}: {sentence title that states the finding}
Message: {one sentence}
On the slide: {content, figures as supplied, "not provided" where missing}
Chart: {none, or what pay-data-charts should draw}
Speaker says: {2 or 3 plain sentences}
Source: {where the user's figure came from}

HARDEST QUESTION: {question}
Honest answer: {from the user's material only}
WHAT WE DO NOT KNOW: {list}

BOARD SUMMARY ({n} words)
The decision: ...  The number: ...  The why: ...  The risk: ...  The ask: ...

NEEDS A HUMAN: {missing figures, unsourced claims, missing dates}
Sign-off: {approver as the user names them}. Not sent to anyone until they approve.
```

Rules:

- Use only figures the user supplies. Never invent a market figure, benchmark, statutory limit, threshold or deadline. Missing means "not provided" on the slide and a line under NEEDS A HUMAN.
- Never smooth over a number that does not add up. Show both versions and ask.
- No tax, legal or regulatory advice. Where equal pay, consultation or pay transparency could matter, say what to check and with whom (counsel, your HR lead). For the EU Pay Transparency Directive, check transposition status and the final rules in your country.
- No vendor names. Say "your HRIS" or "your presentation software".
- Produce an outline, not a design. Make a file of any kind (PowerPoint, Word or other) only if the user asks. A PowerPoint must be real editable text and shapes, never images of slides. Use whatever file tools your Claude has; no custom scripts.
- A human signs off before anything reaches a committee. Show the draft and ask.

## Hand-offs

Run `comp-claim-check` on any market figure before it goes on a slide. Use `pay-data-charts` for any chart. A single person's request is `off-cycle-triage`. Cycle dates and manager guidance are `cycle-planner`.

## Writing rules

British English unless the user writes American. No em or en dashes: use commas, colons, full stops or brackets. Short plain sentences. No filler. Say what the number is, not that it is "significant".
