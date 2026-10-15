# Sample data: promotion-case-checker

Fictional company: Midpoint Ltd. All data is made up for testing.

Files: `level-criteria.md`, `manager-case.md` (Job A), `promotion-list.csv` (Job B, 25 rows).

## What the skill should find

Job A (manager-case.md):
1. Mentoring has no evidence at all: Missing.
2. Influence is only sentiment ("everyone loves working with them"), no decision they changed outside the team: Thin.
3. Tenure, reliability, attitude and late working are used as grounds but are not criteria (the criteria say so).
4. Sustained needs both 2025-H2 and 2026-H1. The case cites one rating and a FY2023 project, which is outside the window.

Job B (promotion-list.csv):
1. Engineering by gender: men 4 of 6 promoted, women 1 of 6. Both groups are 5 or more, so flag it for review, not as a conclusion on cause.
2. Dublin: 2 of 2 promoted. n<5, no conclusion.
3. E2022 appears twice with conflicting outcomes (Y and N). Report it, ask which row stands, do not drop one.
4. E2024 has a blank gender. Report it and exclude from gender cuts only, stating the exclusion.
