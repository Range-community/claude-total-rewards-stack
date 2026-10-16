# Range × Claude: The Total Rewards Stack

**16 free Claude skills covering 32 total rewards jobs, across comp, benefits, stock plan admin, pay data charts and reward comms. One install, about two minutes.**

See all 16 skills on one page: [range.community/resources/total-rewards-stack](https://range.community/resources/total-rewards-stack/).

Built by [Range](https://range.community), a community for reward professionals building with AI. Most of the 32 jobs come in pairs that need the same checks, so one skill does both.

## Install

1. Open the **Claude desktop app** (any paid Claude plan). Don't have it? [Download it here](https://claude.ai/download).
2. Go to **Settings → Capabilities → Add marketplace** and paste:

   ```
   Range-community/claude-total-rewards-stack
   ```

3. Install **total-rewards-stack**. All 16 skills are now live, and they update when we improve them.

**Claude Code:** run `/plugin marketplace add Range-community/claude-total-rewards-stack`, then `/plugin install total-rewards-stack@range-total-rewards-stack`.

**Using claude.ai in a browser?** Click the green **Code** button above, then **Download ZIP**. Each folder in `plugins/total-rewards-stack/skills/` can be zipped and uploaded at claude.ai → Settings → Capabilities → Skills.

There's nothing to configure. Describe the job in plain English and the right skill picks it up.

## Try it on fake data first

Every skill has a practice folder in [`examples/`](examples/) with data from Midpoint Ltd, a company that doesn't exist. Each folder has errors planted in it, and its README lists what the skill should find. Paste the files in, ask for the job, and check Claude catches them before any real pay data goes near it.

## The 32 jobs

| Stage | Skill | Job | Try saying |
| --- | --- | --- | --- |
| **01 Market & pricing** | comp-claim-check | Pressure-test a pay number before anyone acts on it | *Is this number right?* |
| | | Check a survey or vendor claim, cited figures apart from guesses | *Check this benchmark claim before I use it* |
| | job-ad-range-writer | Set the range for a job ad, with the band checked first | *Set the range for this job ad* |
| | | Answer the candidate pay question without asking about pay history | *What do I say when a candidate asks about salary?* |
| **02 Levelling & moves** | promotion-case-checker | Check a promotion case against your level criteria | *Check this promotion case* |
| | | Spot uneven promotion outcomes by team, gender and location | *Check promotion rates by team and gender* |
| | off-cycle-triage | Triage an off-cycle request: options, cost and the knock-on for peers | *Triage this off-cycle pay request* |
| | | Build a retention case from the evidence you supply | *Build a retention case for this person* |
| **03 Pay review cycle** | cycle-planner | Plan the cycle timeline backwards from pay day, with owners | *Plan the merit cycle timeline* |
| | | Write the manager guidance pack, including what not to promise | *Write manager guidance for the pay review* |
| | cycle-upload-checker | Catch errors in the merit upload before payroll | *Check the merit upload* |
| | | Log and justify exceptions before committee | *Build an exceptions log* |
| **04 Fairness & transparency** | pay-gap-pack | Pay gap by category of worker, small groups suppressed | *Run a pay gap by category of worker* |
| | | Explain a gap before you're asked, caveats in | *Draft an explanation of this pay gap* |
| | pay-comms-writer | Write the pay letter from one row of cycle data | *Write the pay letter* |
| | | Answer a pay information request | *An employee asked about their pay level* |
| **05 Benefits** | census-reconciler | Reconcile your HRIS against the provider census | *Reconcile the census* |
| | | Prep a clean renewal data pack with only the fields your broker needs | *Build the census for the broker* |
| | benefits-comms | Build the open enrolment pack: emails, what changed, FAQ, manager brief | *Build the open enrolment pack* |
| | | Triage employee benefits questions: answer from the policy, route the rest | *Triage these benefits questions* |
| **06 Equity & stock plans** | equity-reconciler | Reconcile the grant register against HRIS and payroll | *Reconcile the grant register* |
| | | Track vesting and valuation dates you enter | *Track vesting dates and valuation expiry* |
| | equity-explainer | Explain vesting with scenarios at prices you give, from your plan terms | *Explain this employee's vesting* |
| | | Leaver checklist: what to confirm with plan admin and counsel | *Build a leaver checklist for this grant* |
| **07 Data & decks** | pay-data-charts | Chart where roles or people sit in their pay range | *Chart where each role sits in its range* |
| | | Chart the pay gap and merit spread for committee, counts shown, small groups suppressed | *Chart the merit increase spread by team* |
| | committee-deck-builder | Build the storyline for a pay decision: the ask, evidence, cost and risk | *Build the committee deck for this pay decision* |
| | | Write the one-page board summary | *Write the board summary* |
| **08 Comms & video** | reward-announcements | Write a total reward statement from one person's data | *Write the total reward statement* |
| | | Announce a pay or policy change, with FAQ and what we don't know yet | *Announce the bonus plan change* |
| | reward-video-scripter | Script a 60-second employee explainer, to read aloud | *Script a short video on the pay review* |
| | | Storyboard it with on-screen text and captions | *Storyboard the open enrolment video* |

Most skills will hand you a Word document or Excel workbook if you ask for a file. The video skill writes the script and storyboard only. You record or build the video in your own tool.

## What these skills won't do

- **Make up a number.** No market figure, tax rate, statutory limit, threshold or deadline from memory. If you didn't provide it, the skill says *not provided* and asks.
- **Give tax, legal or regulatory advice.** Where the law matters, the skill tells you what to check and who to check it with. On the EU Pay Transparency Directive, that always means checking transposition status and the final rules in your country.
- **Value equity.** The equity skills don't do tax treatment, valuations or share price predictions, and they won't read meaning into a plan rule beyond quoting the clause you pasted. Every scenario is labelled illustrative, pre-tax, not personalised advice.
- **Send anything.** Every output is a draft. A person signs it off before it reaches an employee, a manager or a committee.

None of it replaces your own pay data, your approval chain or your advisers.

## Your data

Work from employee IDs, not names, and strip anything a job doesn't need (home addresses, bank details, health information). If your employer hasn't approved the tool you're using for pay data, check that first.

## More from Range

- [The Comp AI Library](https://range.community/resources/): free guides, prompts and checklists, including the [Comp Context File](https://range.community/resources/comp-context-file/) and the [Comp Prompt Library](https://range.community/resources/comp-prompt-library/)
- [Range Weekly](https://range.community/newsletter/archive), the newsletter
- [Apply to join Range](https://range.community/community/#signup), the community for reward people building with AI

MIT licence: use it, adapt it, share it. *A community project built for use with Claude; not affiliated with or endorsed by Anthropic.*
