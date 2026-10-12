# Evidence guide: where evidence lives in a PR package

# Evidence guide: where proof lives in a PR package

## Plan fidelity
Where it lives: The plan's scope section (from plan.md or the plan comment) + the PR's diff

What good looks like: The diff's file list matches what the plan said it would change. 
If files differ, plan.md's Deviations section documents why and calls it out.

## Test evidence
Where it lives: The plan's test plan section + the PR description's testing/evidence section

What good looks like: The PR shows concrete before/after output (or logs, or screenshots) that proves the fix works. The evidence matches what the plan said to verify.

## Diff quality
Where it lives: The PR diff (hunks, changed lines)

What good looks like: Each changed line serves the stated issue. No unrelated formatting, refactoring, or cleanup. If debris exists, it's minimal and documented.

## Template compliance
Where it lives: The PR description's structure and all sections

What good looks like: Title, description, test evidence, and disclosure sections are all 
completed with real content (not placeholders). AI-use disclosure is present if applicable.

## Description fidelity
Where it lives: PR description's claims vs. diff contents

What good looks like: What the description says changed matches what the diff shows. 
No silent scope creep or undisclosed changes.
