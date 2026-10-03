# Rubric: is this plan ready to post and build from


## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis matches evidence | Plan's stated cause compared to reproduced evidence | Plan correctly names the same root cause shown in the repro evidence on the issue thread | required |
| Scope is bounded | Plan's scope/change section | Plan describes only the minimum changes needed to fix the root cause; no scope creep or extra refactoring | required |
| Fix targets cause, not symptom | Plan's fix steps + repro evidence | Plan addresses the root cause, not just a workaround or surface-level fix | required |
| Steps are executable | Plan's implementation steps | Steps describe concrete actions that someone could follow; not vague or missing key details | required |
| Test plan is concrete | Plan's testing/verification section | Plan specifies the exact command to run and what success looks like (e.g., "test passes with output X"), not vague ("it works") | required |
| Thread conventions | Plan comment text + repo style guide | Plan comment uses clear, professional language matching the repo's tone; no excessive emoji, vague language, or casual phrasing | required |
| No hidden unknowns | Plan text | Plan acknowledges uncertainties or what it doesn't know; doesn't hide or hand-wave difficult parts | preferred |

## Verdict rule

Accept if: All required checks pass.
Reject if: Any required check fails.
Unclear: Treat as fail and reject.
Preferred checks never change the verdict.