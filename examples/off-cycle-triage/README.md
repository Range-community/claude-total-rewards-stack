# Sample data: off-cycle-triage

Fictional company: Midpoint Ltd. All data is made up for testing.

File: `requests.csv` (8 off-cycle requests). Today's date for this exercise: 2026-10-08. The next cycle effective date is 2027-04-01.

## What the skill should find

1. R3: the requested 99,000 is above the band max of 95,000. Not an off-cycle approval; it is a band or exception decision. (Peers have a median of 84,000, so compression and precedent also need noting.)
2. R5: last increase was 2026-07-01 (about 3 months ago, 5.0%) and the rating is "Below expectations". Decline or hold; "threatens to resign" with no evidence is not a retention case.
3. R6: salary is in USD but the band is in GBP. Data error: flag it, do not convert, no recommendation until fixed.
4. R1 and R4 are "Market" requests with no market source supplied. The skill must not offer a market figure from memory; it should ask for the source and hand off to comp-claim-check. Separately, R2 and R7 have dated flight-risk evidence, so the skill must weigh it rather than call it "no evidence", and state the peer knock-on (R2 asks for 72,000 against a peer median of 69,000). R2 has a written offer and is the strongest case. R7 is only a recruiter approach and already sits above midpoint, so hold to cycle is a fair answer for R7 as long as the evidence is acknowledged.
