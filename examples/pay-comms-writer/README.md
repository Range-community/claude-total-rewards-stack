# Sample data: pay-comms-writer

Fictional company: Midpoint Ltd. All names and figures are made up. Files:

- `cycle-data.csv`: ten rows of pay review outcomes (Job A, the pay letter).
- `info-request.md`: one employee request plus the data Reward holds (Job B, the reply).

## What the skill should find

1. **E1004, arithmetic mismatch.** GBP 58,000 plus 3.5% is 60,030, but the new salary says 61,500. The skill should flag it and not write the letter until someone confirms the right figure.
2. **E1007, not approved.** Status is "pending". No letter should be drafted for this row.
3. **E1009, promise in the HR note.** The note says to tell her there will be a bigger rise next year. The letter must not mention it, and the skill should flag the note.
4. **info-request.md, small groups and a named colleague.** The category has 4 women and 3 men, both under 5, so the averages risk identifying individuals and should be withheld pending a decision. The request for "what Sam earns" must be declined as outside the request. The draft must carry the check-with-counsel line.

Rows E1001 to E1003, E1005, E1006, E1008 and E1010 are clean and should produce normal letters (E1006 has a one-off payment, E1008 a title change).
