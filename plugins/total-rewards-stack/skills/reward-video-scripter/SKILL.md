---
name: reward-video-scripter
description: >-
  Writes a 60-second spoken script for a short employee explainer video on a
  reward topic (pay review, open enrolment, how pay bands work, a new benefit),
  then a storyboard table and a captions block for your video editor.
  Everything comes from the policy text you paste; gaps are listed for a human,
  not filled. It writes words and a plan only, not video. Use whenever someone
  types "script a short video explaining the
  pay review", "storyboard the open enrolment video", "explainer video script
  for employees", "60 second video on our new benefit", "captions for the reward
  video" or "how pay bands work video script".
---

# Reward Video Scripter

Employees watch a 60-second video and skip a four-page PDF. The risk is that a script gets written fast, a deadline is wrong, an allowance is quoted in one currency for everyone, or a cheerful last line sounds like a promise. Spoken words feel more official than written ones, and they are harder to correct once recorded.

This skill writes the script and the storyboard only. It does not render, record or edit video. You take the output into your own video tool, or you record it yourself.

## Before you start: data

Use the policy or plan summary, not individual records. No names, IDs, health details or pay data of real people are needed. If you paste real personal data into a tool your employer has not approved, that is your decision and your risk. To try this first, use `examples/reward-video-scripter/`.

## Step 1: Collect the facts

Ask once for: the topic, the audience (all staff, one site, managers), the policy or plan text, key dates, amounts, who is eligible, where to act, and who to ask. Whoever will read the script aloud should be named, so the lines suit their voice.

Check the pasted text against the brief before writing. List every conflict (two dates, two amounts, a vague eligibility phrase) and every missing item. Do not pick a winner between conflicting facts.

## Step 2: Write the script (Job A)

Write 120 to 150 words, one idea per beat, 6 to 8 beats. Count before you hand over. If under 120, add detail from the pasted text (what the change is, who it covers, how to act), never anything invented. Rules for the spoken line:

- The first sentence says what changes for the viewer.
- Contractions are fine. Sentences are short. One number per sentence at most.
- Define any term in plain words the first time it is used, or cut it.
- End with one next step and who to ask.
- Use only facts from the pasted text or the brief. A missing item is "not provided", not a guess.

## Step 3: Build the storyboard (Job B)

One row per beat. Seconds are estimates at about 150 words a minute (so 120 to 150 words is 48 to 60 seconds) and add up to 60 or under.

- On-screen text is 7 words or fewer.
- On-screen text may only contain figures that appear in the script or the user's input.
- The visual note describes what is shown (a calendar, a simple diagram, the speaker). It names no software.

## Step 4: Check and hand over

Count the words, estimate the read time (words divided by 2.5, in seconds), then tell the user to read the script aloud once, with a timer, and mark any line they trip on. Offer to shorten or reword those lines.

## Output template

```
REWARD VIDEO: {topic}, {audience}

NEEDS A HUMAN
- {conflicts and missing items, each with who can settle it}

SCRIPT ({n} words, about {s} seconds read aloud)
1. {line}
2. {line}

STORYBOARD
| Beat | Seconds | Spoken line | On-screen text | Visual note |
|---|---|---|---|---|
| 1 | 0-8 | {line} | {7 words or fewer} | {what is shown} |

CAPTIONS (timings are estimates, adjust to the recording)
1
00:00:00,000 --> 00:00:04,000
{caption, 2 lines of 42 characters or fewer}

SIGN-OFF: not approved until a named person has checked every figure and date.
```

## Rules

- A human signs off before anything reaches employees. Show the draft and ask.
- Never invent a figure, date, rate, deadline or eligibility rule. Where the pasted text is silent, write "not provided" and list it under NEEDS A HUMAN.
- No promises about future pay, bonus, allowances or coverage. Cut "next year" lines unless a pasted policy clause states them, and then quote it.
- Benefits: never interpret coverage beyond the pasted text. If a viewer might ask "does that include...", the script says who to ask.
- Equity topics: no tax treatment and no valuations. Quote only clauses the user pasted. Any worked scenario carries the label "Illustrative, pre-tax, not personalised advice."
- Do not convert currencies or assume the same number applies in each country. Use the amounts given, per site, or flag the gap.
- No tax, legal or regulatory advice. For the EU Pay Transparency Directive: check transposition status and the final rules in your country.
- Name no video, voice or avatar tools. Give no avatar or voice-clone instructions.

## Hand-offs

Use `benefits-comms` for the written open enrolment pack, and `reward-announcements` for the written announcement and FAQ. Run `comp-claim-check` on any market figure before it is spoken. For vesting explainers, `equity-explainer` holds the grant terms and scenarios.

## Writing rules

British English unless the user writes American. No em or en dashes. Short plain sentences written for the ear. No filler or hype, and no "we are thrilled". Read each line as if saying it to one colleague. If the user wants a file, make a Word document for the script and an Excel file for the storyboard table, using whatever file tools your Claude has.
