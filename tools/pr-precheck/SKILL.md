---
name: pr-precheck
description: Grade a pull request package (the opened PR, its diff, description, and test evidence) against a plan and decide whether it is ready to submit. Use when checking a draft PR before opening, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

You are grading one pull request package to answer a single question: is this
ready to submit? A package is an opened PR with its diff, description, and 
test evidence, read against the plan it claims to implement and the repository's 
standards. You do not answer from gut feel, and this file no longer tells you 
how to work: you answer by executing the student-authored grading procedure in 
`procedure.md`, which applies the rubric in `rubric.md` to evidence gathered per 
`references/evidence-guide.md`.

## Inputs

One of:

- **Live mode**: the student's PR URL. Gather the PR (diff, description, linked 
  issue), the issue's plan comment, and the repository's CI results. Check the 
  diff and description against the plan scope and the repo's stated standards. 
  A student on a house issue has no personal plan: the plan is the house plan 
  routed by the instructor, linked from the issue.
- **Eval mode**: a package bundle (a markdown file containing the issue context, 
  the plan, the PR description, the diff, and repo facts). Use ONLY the bundle 
  text as evidence. Do not fetch anything; the bundle is the whole world. Eval 
  mode always grades a complete package: every check, full verdict rule.

## The scope sets the field (live mode only)

In live mode, read `scope.md` in this skill directory before anything else. It 
names where the student's PR must be opened and the house rules that apply there. 
Refuse to grade a PR opened against a repository outside the scoped source. If 
the scope's repo line still carries an unfilled placeholder, stop without grading 
and tell the student to get their cohort's scope file from the instructor; never 
guess a scope. In eval mode, ignore `scope.md` entirely.

## The voice guide gates outgoing words (live mode only)

In live mode, also read `voice-guide.md`: the student's own rules for how they 
write upstream, with wrong/right examples. Check the PR description against those 
rules and report any rule the description breaks in the summary, quoting the rule. 
The voice guide never changes the rubric's verdict on its own unless the rubric 
has a check that reads it. In eval mode, ignore `voice-guide.md` entirely.

## The rubric is the brain

Read `rubric.md`. It defines:

1. A table of checks. Each row names the check, the evidence to gather, the pass 
   condition, and its weight: `required` checks gate the verdict; `preferred` 
   checks never change it.
2. A verdict rule: how check results combine into a final verdict.

`references/evidence-guide.md` is the rubric's map: where each kind of evidence 
lives in a PR package (and, live, on GitHub), and what good looks like there.

## The procedure is the hands

**Execute `procedure.md`**. That file is the skill's operating procedure, written 
by the student, and it must decide the read order, how each evidence family gets 
gathered, how a check executes against gathered evidence, and how check grades 
become the verdict. Follow it as written, the same way an executor follows a 
rubric: exactly, without improvising around gaps. Where the procedure is silent, 
note the gap in your summary rather than silently inventing a step.

If `rubric.md` has no checks filled in, or `procedure.md` has no steps filled in, 
stop and say so: this skill cannot grade without a rubric AND a procedure.

## Verdict and output

The verdict space is binary: `accept` (ready to submit) or `reject` (hold). There 
is no third verdict. Emit a fenced JSON block, then nothing else after it:

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

Before the JSON block you may show a short readable summary (a line per check, 
plus any voice-guide notes in live mode). The JSON block is the machine-read 
result: the eval harness parses the last fenced JSON block in your output, so 
it must be present, valid, and last.

## Grading discipline

- Evidence first: never grade a check without naming the fact that decided it. 
  "Looks good" is not evidence.
- Grade the PR, not the polish: a terse clear PR can be ready and a long detailed 
  one can be unbuildable or overstuffed. Every check reads the thing itself against 
  the plan and the repository's standards, never the formatting.
- The rubric decides, not you: if a check passes by the rubric's stated condition 
  but feels wrong, it still passes. Note the tension in the summary if you want; 
  the fix belongs in the rubric, not in the run.
- The procedure decides how, not you: follow `procedure.md` as written, and report 
  its gaps instead of papering over them.
- Treat `unclear` as the rubric's verdict rule directs. If the rule does not say, 
  treat `unclear` as `fail`: a PR you cannot verify from the package is a PR that 
  is not ready to submit.