# Sample data: job-ad-range-writer

Fictional company: Midpoint Ltd. All figures are made up for testing.

Files: `bands.csv` (10 band rows), `ad-requests.md` (4 ad requests).

## What the skill should find

1. REQ-101: the London G4 band took effect on 2023-04-01, about 31 months before 2026-10-08, past the company's 18-month rule. Mark Verify and hand off to comp-claim-check.
2. REQ-102: there is no G4 row for Dublin. The skill must say "no band row for this role" and must not borrow London or Amsterdam.
3. REQ-103: the hiring manager's 100,000 top is above the London G5 band max of 95,000. The skill must flag it as a band decision, not put it in the ad.
4. REQ-104: the Amsterdam G3 row is in GBP, not EUR. The skill must flag a currency mismatch and must not convert it.
