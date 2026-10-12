# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity | Diff's changed files vs. plan's scope section | Changed files are exactly those named in the plan, or deviations are documented in plan.md's Deviations section | required |
| Test evidence shown | PR description's test section vs. plan's test plan | PR description includes before/after outputs matching the planned verification steps | required |
| Diff is focused | Diff hunk content | Changed lines serve the stated issue; no unrelated refactoring, formatting, or debris | required |
| Template compliance | PR description structure | All template sections completed with concrete content, including AI-use disclosure if applicable | required |
| Description matches diff | PR description claims vs. diff contents | What the description says changed matches what the diff shows | required |

## Verdict rule

Accept if: All required checks pass.
Reject if: Any required check fails.
Unclear: Treat as fail and reject.