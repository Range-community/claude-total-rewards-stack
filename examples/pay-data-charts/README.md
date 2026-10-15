# Sample data: pay-data-charts

Fictional data for Midpoint Ltd. Not real people, not real pay. Employee IDs only, no names.

## Files

- `roles-and-bands.csv`: 20 people with role, team, location, currency, annual base pay as a full-time equivalent, and the band minimum, midpoint and maximum for the role. Use it for "where do people sit in their pay range".
- `merit-outcomes.csv`: 24 people with team, rating and merit increase %. Use it for "show the merit spread by team or rating". These are a different set of people from the first file.
- `gap-results.csv`: pay gap results by category of worker, in the shape `pay-gap-pack` produces (gap = men minus women, divided by men). Use it for "chart the pay gap for committee". It matches the answers in `examples/pay-gap-pack/`.

## Try saying

- "Chart where each role sits in its pay range, using roles-and-bands.csv."
- "Show compa-ratio by team with the band on it."
- "Chart the merit increase spread by team and by rating for the committee."
- "Chart these pay gap results by category of worker for the reward committee."
- "I want a chart of our pay gap but I have no numbers yet." (the skill should hand off to `pay-gap-pack`)

## What the skill should find

Roles and bands:

1. **Mixed currencies:** GBP, EUR and USD in one file. The skill must stop and ask how to put pay and bands on a common basis (one currency with rates you supply, one chart per currency, or a position-only view that uses no currency). It must not plot raw amounts together or invent an exchange rate.
2. **One person above the band maximum:** E2006 (Software Engineer) is paid above the 75,000 band maximum. Flag by ID in "needs a human". Do not plot the person's pay as a point.
3. **One category with n<5:** Operations Coordinator has 3 people. Show the band and "suppressed, n<5". No median marker, no position.
4. **One row with no band:** E2020 (Account Executive) has no band minimum, midpoint or maximum. Leave out of the chart, count it as "not provided: 1", and ask. Account Executive then rests on 5 people with a band; say so.

Merit outcomes:

5. **Data team has 4 people** and the Developing rating has 3. Both are suppressed, n<5, in the team and rating views.
6. **E2120 has no rating.** Show "not provided: 1", leave out of the rating view, keep in the team view.

Pay gap results:

7. **Data L4 has 1 woman and 3 men** but a gap of 4.3% is supplied. The skill must suppress it, not plot it.
8. **Operations L2:** mean gap 8.7% and median gap 0.0% differ sharply. The chart should show both, and the caption must not claim a single gap figure.

## What the skill should NOT do

- Plot any one person's pay or increase.
- Start an axis above zero to make a gap look larger, or draw a threshold line the user did not supply.
- Call any outcome fair, unfair, justified or unlawful.
- Show a chart to a committee without asking the user to approve the draft.
