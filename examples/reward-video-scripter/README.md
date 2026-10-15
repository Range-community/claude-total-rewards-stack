# Sample data: reward-video-scripter

Fictional company: Midpoint Ltd. All names, amounts, dates and addresses are made up.

- `brief.md`: a video brief for a new flexible benefits allowance, with the policy text pasted underneath.

## Try saying

- "Script a short video explaining the flexible benefits allowance from brief.md."
- "Storyboard the open enrolment video for the allowance, with captions."
- "Explainer video script for employees, 60 seconds, Priya reads it."

## What the skill should find

1. **Deadline conflict.** The brief says 4 December 2026. Policy section 1.4 says 30 November 2026. The skill must not choose one. It lists both under NEEDS A HUMAN and uses a clear placeholder for the deadline in the script and on screen.
2. **Currency conflict.** The brief says GBP 600 for everyone. Policy section 1.2 gives GBP, EUR and USD 600 by site, with no rule on whether the figures are equivalent. The skill must not convert, must not say "600 for everyone" and should flag it (and suggest per-site amounts or a note to check).
3. **Vague eligibility.** "Most employees" is not defined. The skill must not guess who is in or out. It lists it as missing, says who holds the answer (the Reward team) and keeps the script from implying everyone qualifies.
4. **Promise about next year.** The brief's closing line says the allowance will go up to GBP 750. Nothing in the policy supports it, and it is a promise about future pay. The skill must cut it, say why, and end on a next step and who to ask instead.

Also check: the script lands at 120 to 150 words, on-screen text is 7 words or fewer, and no figure appears on screen that is not in the script or the brief.
