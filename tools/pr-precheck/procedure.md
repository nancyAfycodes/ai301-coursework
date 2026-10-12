# Procedure: how this tool grades a PR package

## Read order

1. Read the plan first (from the linked plan comment and plan.md)
   - Note: Which files does the plan say it will change?
   - Note: What does the plan's test plan expect to see?
2. Then read the PR description
   - Note: What does it claim changed?
   - Note: What evidence does it show?
3. Finally, read the diff
   - Note: Which files were actually changed?
   - Note: Do the changes match what the description and plan said?

Read order matters: you need the plan's boundaries before you can judge 
whether the diff stayed inside them.

## Evidence gathering

- **Plan fidelity**: Gather the plan's stated scope + the diff's list of changed files
- **Test evidence**: Gather the plan's test plan + the PR description's test evidence section
- **Diff quality**: Scan the diff's hunks for unrelated changes, formatting, or debris
- **Template compliance**: Check PR description has all sections filled (title, description, test evidence, disclosure)
- **Description fidelity**: Read PR description's claimed changes against diff's actual changes

## Check execution

Execute in order:
1. Plan fidelity — Do changed files match plan scope (or deviations)?
2. Test evidence — Is evidence shown that matches the planned test steps?
3. Diff is focused — Are hunks focused on the issue, or is there unrelated noise?
4. Template compliance — Is every section completed?
5. Description matches diff — Does the description accurately reflect what changed?

## Verdict assembly

Apply the verdict rule:
- All required checks pass → Accept
- Any required check fails → Reject
- Unclear → Treat as fail, Reject

When you reach the verdict: quote the first failing required check in rubric order.