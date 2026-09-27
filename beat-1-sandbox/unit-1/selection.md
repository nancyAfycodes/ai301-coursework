# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71",
  "checks": [
    {"name": "Repo is active", "grade": "pass", "evidence": "Last default-branch commit 2026-09-16 by Andrew Burke, 11 days before today (2026-09-27)"},
    {"name": "Manageable scope", "grade": "pass", "evidence": "Body states the cause (eight-space indent parsed as a code block), the fix, the xfail marker to remove, and the two relevant files"},
    {"name": "Not already claimed", "grade": "pass", "evidence": "Comments API returns an empty array; no assignee and no linked PR"}
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

7/13 scored items
10/13 scored items
12/13 scored items
15/20 scored items
17/20 scored items
16/20 scored items

**Issue analysis**
I picked issue-05
issue-05: Your rubric decided reject (failed "Not already claimed"), but the gold label was accept. 
Your rubric's reasoning: the issue appeared to have active engagement in comments. However, looking at the evidence, 
the issue actually had no assignee and no linked PR, which should have triggered an accept. The rubric may be 
interpreting "claimed" too broadly based on comment activity.

**Check rationale**

"Issue has a description of the task, regardless of complexity level"

This check prioritizes clarity of description over complexity. The reasoning is that a newcomer can handle any scope 
if the task is clearly explained. A well-documented hard problem is more accessible than a vague easy one.

**Trade-offs**

This check accepts issues with clear descriptions even if they're complex, which means some genuinely hard issues 
get accepted. For example, issue-13 was rejected by my rubric but accepted by the gold label, suggesting the rubric 
misses cases where a complex issue is still appropriate for a first contributor if there's mentorship available.
---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. Fit to interests and time: Issue #71 is a small, focused fix (removing indentation and an xfail marker). It requires minimal context and fits my schedule for a first issue.

2. What the verdict identified correctly: My skill correctly identified that the repo is active, the scope is manageable (clear fix described), and the issue is unclaimed (empty thread). I weighted the "no competition" aspect  and noted that this issue hasn't been claimed, which reduces coordination complexity.

3. Anticipated difficulty: Low. The fix is localized to two files, the change is straightforward, and there are no competing claims. The main challenge is understanding the test fixture structure before making any fixes to the issue.
---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
