# Procedure: how this skill grades a plan package

## Read order

1. Start with the reproduced evidence (unit 2: repro-report.md and claim comment)
   - Note: What is the root cause named in the conclusion?
   - Note: What behavior does the error output show?
2. Then read the plan comment/document
   - Note: What cause does the plan state?
   - Note: What specific changes does it propose?

Read order matters: you need to know what the repro proved before you can judge 
whether the plan matches it.

## Evidence gathering

For each check:
- **Diagnosis matches evidence**: Gather the issue's reproduced evidence (from GitHub comments/thread) + the plan's stated cause
- **Scope is bounded**: Gather the plan's "Scope" section
- **Fix targets cause**: Gather the repro evidence's root cause + plan's fix approach
- **Steps are executable**: Gather the plan's implementation steps (numbered list)
- **Test plan is concrete**: Gather the plan's verification/testing section
- **No hidden unknowns**: Scan the plan for vague language or hand-waving

## Check execution

Execute in order:

1. Diagnosis matches evidence — Compare plan's stated cause to repro report's conclusion. 
   Are they naming the same root cause?
2. Scope is bounded — Does the plan list only the minimum changes? Any refactoring or extras?
3. Fix targets cause — Does the plan fix the root cause or work around the symptom?
4. Steps are executable — Could a stranger follow these steps? Are they specific (file names, line numbers)?
5. Test plan is concrete — Is the test command exact? Does it specify passing vs. failing output?
6. No hidden unknowns — Does the plan acknowledge anything uncertain or difficult?

## Verdict assembly

Apply the verdict rule:
- All required checks pass → Accept
- Any required check fails → Reject
- Unclear grades → Treat as fail, Reject
- Preferred checks never change the verdict

When you reach the verdict:
- If Accept: state "Plan is ready to execute"
- If Reject: quote the check that failed and why
