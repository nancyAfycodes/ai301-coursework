# Building Reusable Evaluation Tools for Open Source Contributions

## Overview

Built a four-tool framework (issue-select, repro-check, plan-check, pr-precheck) to guide myself through the full open source contribution lifecycle: selecting a good first issue, reproducing a bug, planning a fix, and evaluating the final pull request. The problem I solved for myself: contributing to open source requires structured thinking at every phase; without standards, it's easy to miss critical details or submit work unprepared. I designed rubrics, procedures, and evidence guides for each phase, iterating based on feedback—replacing fuzzy criteria with observable facts. The outcome: opened [PR #86](https://github.com/codepath/pathreview-ai301-fa26-s3/pull/86) that fixed a test fixture indentation issue in a live repository, and achieved perfect agreement (20/20) when my evaluation framework graded contributions.

## What happened

### Proof 1: The Bug I Reproduced (Unit 2)

The failing test showed the root cause clearly:

```
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy FAILED    [ 66%]

self = <tests.unit.test_readme_parser.TestReadmeParser object at 0x...>
parser = <ingestion.parsers.readme_parser.ReadmeParser object at 0x...>

    def test_extract_heading_hierarchy(self, parser):
        """Test heading hierarchy extraction."""
        markdown = """
    # Main Title
    Some content

        ## Subsection
        More content

        ### Sub-subsection
        Even more content

        ## Another Section
        Final content
        """
        headings = parser._extract_heading_hierarchy(markdown)

        assert isinstance(headings, list)
>       assert len(headings) > 0
E       assert 0 > 0
E        +  where 0 = len([])

tests\unit\test_readme_parser.py:152: AssertionError
```

The parser returned an empty list because the fixture's 8-space indentation made Markdown parse it as a code block instead of content.

### Proof 2: The Rubric Change (Unit 3 → Unit 4)

**My first criterion (Unit 3):**
```markdown
| Test plan is concrete | Plan's testing/verification section | Plan specifies the exact command to run and what success looks like (e.g., "test passes with output X"), not vague ("it works") | required |
```

The problem: "concrete" meant different things to different evaluators. What counts as "concrete" for one project (a full pytest run) isn't the same for another (a CI check or manual observation). The rubric didn't account for this variation.

**My revised criterion (Unit 4):**
```markdown
| Test plan is stated | Plan's testing/verification section | Plan describes how to verify the fix works (whether as a command, CI check, manual steps, or observation) | required |
```

By replacing the vague word "concrete" with an observable condition ("describes how to verify"), the rubric now accepts multiple valid verification approaches instead of rejecting them for not being "concrete enough."

### Proof 3: The PR I Opened (Issue #71)

**[PR #86](https://github.com/codepath/pathreview-ai301-fa26-s3/pull/86):** Fix issue #71: Remove indentation from heading hierarchy test fixture

**What changed in the code:**

```diff
-   @pytest.mark.xfail(
-       strict=True,
-       reason="issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings"
-   )
    def test_extract_heading_hierarchy(self, parser):
        """Test heading hierarchy extraction."""
        markdown = """
-   # Main Title
-   Some content
-
-       ## Subsection
-       More content
+# Main Title
+Some content
+
+## Subsection
+More content
```

The red lines show the **indented fixture (broken)**—Markdown parsed it as a code block.  
The green lines show the **dedented fixture (fixed)**—now Markdown correctly extracts headings.

**After the fix:**
```
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED    [ 66%]
================================== 14 passed, 1 xfailed in 0.40s ==================================
```

All 5 CI checks passed (frontend, lint, test-integration, test-unit, typecheck). The PR is open and ready for maintainer review.

### Proof 4: Evaluation Framework Results

My final eval run on 20 test packages showed:

```
agreement: 20/20 scored items  (bar: 18/20: PASS)
categories: clear-accept 7/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3
```

This means my rubric correctly identified all 20 packages as accept or reject, matching expert opinion on every single case. The revised criterion (observable facts instead of vague adjectives) works across all review types: clearly correct accepts, boundary cases, edge cases where behavior shifts silently, standards violations, and unreviewable changes.

## Limitations and what's next

### Limitations

The four-tool framework was built and tested exclusively within a controlled sandbox environment on 20 evaluation packages from the course. While the 20/20 agreement demonstrates strong internal consistency, the framework hasn't yet been applied to real-world open source contributions outside this class. Different projects may have different cultures, contribution styles, and standards that could reveal gaps in my rubrics or procedures.

Additionally, the framework focuses on individual contributor workflows (issue → reproduction → plan → PR review). It doesn't yet address scenarios like co-authored fixes, long-running refactors, or contributions to unfamiliar codebases where the problem statement itself is ambiguous.

### What's next

The natural next step is to apply these tools to real open source projects — both as a contributor following my own framework to stay disciplined, and as a reviewer using my pr-precheck rubric to evaluate other PRs. Real-world testing will reveal which rubric checks are universal and which need context-specific tweaks.

Beyond that, I want to expand the framework to handle more complex contribution scenarios: working with maintainers across multiple review rounds, contributing to projects with unfamiliar tech stacks, and building tools (like my four-tool framework itself) rather than just fixing bugs. Each scenario will refine how I think about structured contribution work.
