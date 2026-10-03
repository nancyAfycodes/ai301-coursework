# Evidence guide: where evidence lives in a plan package

## Diagnosis
Where it lives: The plan's "Root Cause" section, compared against the issue's reproduced evidence (GitHub comments).

What good looks like: The plan names the same root cause the repro evidence shows. 
For issue #71, that's the 8-space indentation parsed as a code block.

## Scope
Where it lives: The plan's "Scope" section.

What good looks like: The plan lists only the minimum changes. No extra refactoring or feature scope.

## Executability
Where it lives: The plan's "Implementation Steps" section.

What good looks like: Steps are numbered, specific (file names, line numbers), and a stranger could follow them.

## Test plan
Where it lives: The plan's "Testing & Verification" section.

What good looks like: Specifies the exact command to run and what passing output looks like.

## Honesty
Where it lives: The plan's "Unknowns & Notes" section.

What good looks like: Plan acknowledges what it doesn't know; doesn't hide difficult parts.

## Comms
Where it lives: The plan comment posted on the GitHub issue.

What good looks like: Language is clear, specific, professional. Matches the repo's contribution style.