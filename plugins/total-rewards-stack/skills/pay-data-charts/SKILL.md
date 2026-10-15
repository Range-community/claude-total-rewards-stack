---
name: pay-data-charts
description: >-
  Turns pay data you already have into clear charts: where roles or teams sit in
  their pay range (compa-ratio and range position, with the band shown), and
  committee-ready charts of pay gap results by category of worker and the merit
  increase spread by team or rating. Every group shows its headcount and groups
  under 5 are suppressed. You get an Excel workbook with native charts, or one
  HTML file. Use whenever someone
  asks to chart compa-ratio, show range position, plot people against the band,
  draw a band chart, chart the pay gap for committee, make a merit spread chart,
  or graph increases by team or rating.
---

# Pay Data Charts

A pay chart gets looked at for ten seconds and quoted for a year. The usual failures are a truncated axis that makes a small gap look large, a bar for a team of two that identifies them, and mixed currencies on one axis. This skill picks the right chart, keeps it honest, and says what it does not show.

## Before you start: data

Use employee IDs, never names. Keep only: ID, role or team, currency, annualised full-time equivalent base pay, band minimum, midpoint and maximum, and for merit: rating and increase %. Leave out dates of birth, addresses, health information and bank details.

If you are about to paste real personal data into an AI tool your employer has not approved, check that first. If you choose to carry on, that is your call and I will work with what you give me.

To try it first, use the sample data in `examples/pay-data-charts/`.

## Step 1: Pick the job and confirm the basics

Ask only what blocks the chart.

- **A. Position in range:** by role or by team? Pay element: base by default.
- **B. Gap or merit for committee:** gap by category of worker, merit spread by team, or merit spread by rating?
- **Pay gap numbers:** if you have none yet, stop and use `pay-gap-pack` first. Do not calculate a gap here.
- **Band minimum, midpoint and maximum:** they come from your data. If missing, write "not provided" and ask. Never infer a band from the pay you can see.
- **Currency:** if rows mix currencies, stop before drawing anything, even if a position-only view looks obvious. You may recommend one, but the user chooses. Do not plot raw amounts together. Ask which you want: one currency using exchange rates you supply, one chart per currency, or a position-only view (compa-ratio and range position are ratios and need no conversion, if pay and band are in the same currency on each row). Never supply a rate yourself.

## Step 2: Prepare the numbers

- Compa-ratio = pay divided by band midpoint. Range position = (pay minus band minimum) divided by (band maximum minus band minimum), so 0% is the minimum and 100% the maximum.
- Group by role or team. For each group show n, median compa-ratio and median range position. Medians, not individual points.
- **Suppress any group under 5.** Show the band and the count, and write "suppressed, n<5". No median, no position, no spread. Never plot one person's pay or increase.
- Count people with no band, no rating or no gender as "not provided" and leave them out. Say how many.
- People outside the band: report them by ID to the user in NEEDS A HUMAN, with no pay figure. Do not put names or IDs on the chart.

## Step 3: Choose the form from the question

| Question | Chart |
|---|---|
| Where do roles or teams sit in their range? | One row per group: a grey bar from band minimum to maximum, a tick at the midpoint, one accent marker at the group median |
| How big is the pay gap by category? | Horizontal bars of gap % from a zero line, mean and median, n women and n men on each row |
| How much did increases vary? | Per team or rating: median increase with the 25th to 75th percentile range, n on each row |

One headline number is a number, not a chart. Compare close values with bars, never pie charts.

## Step 4: Chart rules

- **One accent colour, greys for everything else.** Accent marks what the title is about. Never use colour as the only signal: flags also carry a word.
- **Title states the finding, not the topic.** "Engineers sit in the upper half of their band" beats "Range position by role". Check the title against the numbers.
- **Bars start at zero.** Never truncate an axis to exaggerate a gap. A range chart shows position, so it may use a fitted scale, but label it. A zero line is always drawn on gap charts.
- **Label directly** on bars and points. Axes carry units and currency, for example "Gap, % of men's pay" or "Annual base pay, GBP FTE". Add a legend only if two or more series need it.
- **Show n on every row.** Sort by the value shown or a natural order (level), and say which. Suppressed rows sit at the bottom in grey.
- **Threshold lines only if the user gave the number.** Mention the EU Pay Transparency Directive uses 5% for a joint pay assessment, and tell them to check transposition status and the final rules in their country.
- **Readable:** text at least 11 pt, strong contrast on a white background, and a data table beside the chart for anyone who cannot read colour.

## Step 5: Build the file

With file tools, make an Excel workbook: a Data sheet, a Chart sheet with native charts (a range bar is a stacked bar with an invisible first series), and a Notes sheet. Without file tools, write one self-contained HTML file with inline SVG, no external links. Either file, including the Data sheet, holds group results only: never the raw rows, employee IDs or one person's figure, not even in hidden data or script. Put the one-line caption under each chart. Show the user the draft and ask before calling it final.

## Output template

```
PAY DATA CHARTS: {date} · Job: {A range position / B gap / B merit} · Basis: {currency or position-only}
Source: {file} · Suppression: groups under 5

CHART {n}: {title that states the finding}
{chart, or sheet and cell range where it sits}
Says: {one line}. Does not say: {one line, for example whether any pay is fair or justified}.
Method: {formula used} · Axis: {starts at zero / fitted and labelled}

| Group | n | Median compa-ratio | Median range position | Note |
|---|---|---|---|---|
| ... | ... | ...% | ...% | Suppressed, n<5 / OK |

Not provided: {count and reason}, left out.
NEEDS A HUMAN: {IDs outside the band, missing bands, currency choice, title wording}
SIGN-OFF: Draft only. Not for committee or employees until you approve.
```

Rules:

- Never invent a number, benchmark, threshold, exchange rate or band. Everything comes from the user's data.
- No tax, legal or regulatory advice. For the EU Pay Transparency Directive, always say "check transposition status and the final rules in your country".
- No vendor names. Say "your HRIS" or "your payroll export".
- Suppress every group under 5. Never reveal pay or an increase for one person.
- Never call a result fair, unfair, justified or unlawful. That is for counsel.
- A human signs off before a chart reaches a committee, manager or employee. Show the draft and ask.

## Hand-offs

Use `pay-gap-pack` to calculate the gap before charting it. Use `cycle-upload-checker` if the increases themselves may contain errors. Run `comp-claim-check` on any market figure or band before it goes on a slide.

## Writing rules

British English unless the user writes American. No em or en dashes, including in ranges: write "0 to 100%". Short plain sentences, no filler. Captions are one line each.
