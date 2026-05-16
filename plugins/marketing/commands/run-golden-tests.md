---
description: Re-run every Golden Test against the current agent set and summarize regressions.
---
Run every active Golden Test on this workspace. For each one, compare the new run's artifact against the saved baseline using the side-by-side diff. Report:

- Tests that passed (briefly).
- Tests with material regressions: name, what diverged, suspected root cause.
- Tests with cosmetic differences only: name, what changed, whether the baseline should be updated.

End with a one-line recommendation: ship / hold / promote new baselines.
