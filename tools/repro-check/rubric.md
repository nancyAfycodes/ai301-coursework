# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Repo is active | Claim comment and repro report | Repo's last commit is recent (within 60 days) | required |
| Environment recorded | Repro report's setup section | Environment details are present (Python version OR test framework OR system info) | required |
| Steps are complete | Repro report's steps section | Steps are provided and describe how to trigger the issue | required |
| Behavior shown | Repro report's output section | Output shows a concrete error or problem with the reported issue; not a different error type | required |
| Not wrong-target issue | Repro report's conclusion | Report confirms this is the stated issue, not a different bug | required |

## Verdict rule

Accept if: All required checks pass.
Reject if: Any required check fails.
Unclear: Treat as fail and reject.
