---
name: promotion-case-checker
description: >-
  Checks a manager's promotion case against your own level criteria and shows where the
  evidence is strong, thin or missing, with the questions to send back. Also reads a
  promotion list export and flags uneven promotion rates across teams, genders and
  locations, with counts and a small-number warning. Use whenever someone asks to check a
  promotion case, test a promotion nomination, compare evidence to level criteria, review
  promotion justifications, check promotion rates by team or gender, or spot uneven
  promotion outcomes before a calibration or committee.
---

# Promotion Case Checker

Promotion cases fail in two ways. A weak case gets through because the manager is persuasive, or a strong case dies because it was written badly. And the list of outcomes can look fair case by case while the pattern is not. This skill tests each case against your criteria, and then tests the list.

## Before you start: data

Use employee IDs, not names. Strip anything not needed: home address, health or leave details, bank details, ratings history beyond what the criteria need. If your employer has not approved this tool for people data, check first; if you choose to carry on, the skill will work with what you give it. To try it first, use `examples/promotion-case-checker/` (fictional criteria, one manager case, one promotion list).

## Job A: Check one promotion case

### Step 1: Gather

Draft from what the user gave. You need the level criteria (their framework, pasted) and the manager's case. If the criteria are not provided, ask for them. Do not use a generic ladder.

### Step 2: Test each criterion

For each criterion, find the manager's evidence and rate it:

- Evidenced: a specific piece of work, with a date and an outcome
- Thin: asserted, general or one example for a criterion that needs a pattern
- Missing: nothing in the case addresses it

Quote the manager's words. Flag anything used as grounds that is not a criterion (tenure, effort, attitude, "everyone likes them"). Flag evidence outside the review window the criteria set. If the criteria need sustained performance, count the periods shown.

### Step 3: Output

```
PROMOTION CASE: Employee {ID}, {from level} to {to level}
Window: {review period the criteria set, or "not provided"}

| Criterion | Manager's evidence (quoted) | Rating | Gap or question |
|---|---|---|---|

Not criteria, but used as grounds: {list, or "none"}
Strongest part of the case: {one line}
Biggest gap: {one line}
Questions for the manager:
1. {specific question that would close a gap}

Reading: {Ready for committee / Needs more evidence / Not yet}, with the reason.
Approval: this is a check, not a decision. The manager and committee decide.
```

## Job B: Spot uneven promotion outcomes

### Step 1: Prepare the list

Expect one row per eligible employee with team, location, gender, eligible, and promoted. Before counting, report data problems: duplicate IDs (list both rows), blank fields, anyone promoted but not marked eligible. Do not silently drop or fix rows. Ask which duplicate row stands.

### Step 2: Count

Promotion rate = promoted divided by eligible, for each group the user names (team, gender, location, level), one cut at a time, then gender within each team. Show counts, not just percentages: "4 of 6".

### Step 3: Flag, carefully

- Any group with fewer than 5 people: show the count and write "n<5, no conclusion". Do not rank it or call it a pattern.
- For groups of 5 or more, flag differences the user's threshold calls for. If they give none, still show every cut with its counts, list the largest differences as "for review, threshold not provided", and ask for one. Do not set one.
- Blank values (no gender, no team): leave those rows out of that cut only, and say how many were left out under the table.
- Every count in a flag must match the table. Recheck before writing it.
- A flag means "look at this", not "this is bias" and not "this is fine". Name two or three things to check (eligibility rules, who was nominated, calibration notes).

```
PROMOTION PATTERN CHECK
Data issues: {list}
| Group | Eligible | Promoted | Rate | Note |
|---|---|---|---|---|
Flags: {group, counts, gap, what to check next}
Small groups (n<5): {group, counts, no conclusion}
Approval: for HR and the committee chair to review. Not for sharing with managers as a finding.
```

Rules:

- Never invent a market figure, statutory limit, threshold or deadline. If the user has not given a flag threshold, ask.
- No legal or regulatory advice. Promotion rates by sex or protected group can carry legal weight. Say what to check and with whom (counsel, your HR lead). For EU roles, check transposition status of the Pay Transparency Directive and the final rules in your country.
- Judge only against the criteria pasted. Never add criteria.
- A human signs off before anything reaches a manager, employee or committee. Show the draft and ask.

## Hand-offs

If the case rests on a pay or market claim, run `comp-claim-check`. If a promotion triggers a pay move, `off-cycle-triage` handles the request.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences. No filler. If the user wants a file, produce Excel for tables and Word for documents with whatever file tools their Claude has.
