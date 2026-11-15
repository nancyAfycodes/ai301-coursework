# Building Reusable Evaluation Tools for Open Source Contributions

## Overview

Built a four-tool framework (issue-select, repro-check, plan-check, pr-precheck) to guide myself through the full open source contribution lifecycle: selecting a good first issue, reproducing a bug, planning a fix, and evaluating the final pull request. The problem I solved for myself: contributing to open source requires structured thinking at every phase; without standards, it's easy to miss critical details or submit work unprepared. I designed rubrics, procedures, and evidence guides for each phase, iterating based on feedback—replacing fuzzy criteria with observable facts. The outcome: shipped a real PR (#86) that fixed a parsing bug in a live repository, and achieved perfect agreement (20/20) when my evaluation framework graded contributions.

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

### Proof 2: The Feedback That Changed Everything (Unit 3 → Unit 4)

**Unit 3 Feedback:**
> "Replace subjective adjectives with observable facts... 'concrete content,' 'debris,' 'accurately reflect' force the grader to guess what you meant."

**My First Attempt (Unit 3):**
```markdown
| Test plan is concrete | Plan's testing/verification section | Plan specifies the exact command to run and what success looks like (e.g., "test passes with output X"), not vague ("it works") | required |
```

This was too strict. In Unit 4 eval runs, it rejected good PRs because different projects verify fixes differently.

**My Fix (Unit 4):**
```markdown
| Test plan is stated | Plan's testing/verification section | Plan describes how to verify the fix works (whether as a command, CI check, manual steps, or observation) | required |
```

This accepted multiple valid verification approaches.

**The Result:**
- Run 1 (fuzzy criteria): 17/20 ❌
- Run 2 (loosened criteria): 19/20 ⬆️
- Run 3 (refined approach): **20/20 perfect** ✅

### Proof 3: The PR That Shipped (Unit 3)

**PR #86:** https://github.com/codepath/pathreview-ai301-fa26-s3/pull/86

**Title:** Fix issue #71: Remove indentation from heading hierarchy test fixture

**Changes made:**
- Removed 8-space indentation from the markdown fixture string in `test_extract_heading_hierarchy`
- Removed the `@pytest.mark.xfail` decorator (lines 134-137)
- Test fixture now correctly parses heading hierarchy

**Before:**
```
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy FAILED
assert 0 > 0 (empty heading list)
```

**After:**
```
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED    [ 66%]
================================== 14 passed, 1 xfailed in 0.40s ==================================
```

All CI checks passed (lint, frontend, test-integration, test-unit, typecheck).

### Proof 4: What Landed Because of My Work

1. **PR #86 was accepted and merged** — the fix is now live in the repository
2. **My evaluation framework achieved perfect agreement (20/20)** — all categories passed when grading contributions
3. **The lessons traveled forward** — the principle "observable facts, not adjectives" applied across all four tools and became the foundation for success

## Limitations and what's next

### Limitations

The four-tool framework was built and tested exclusively within a controlled sandbox environment on 20 evaluation packages from the course. While the 20/20 agreement demonstrates strong internal consistency, the framework hasn't yet been applied to real-world open source contributions outside this class. Different projects may have different cultures, contribution styles, and standards that could reveal gaps in my rubrics or procedures.

Additionally, the framework focuses on individual contributor workflows (issue → reproduction → plan → PR review). It doesn't yet address scenarios like co-authored fixes, long-running refactors, or contributions to unfamiliar codebases where the problem statement itself is ambiguous.

### What's next

The natural next step is to apply these tools to real open source projects — both as a contributor following my own framework to stay disciplined, and as a reviewer using my pr-precheck rubric to evaluate other PRs. Real-world testing will reveal which rubric checks are universal and which need context-specific tweaks.

Beyond that, I want to expand the framework to handle more complex contribution scenarios: working with maintainers across multiple review rounds, contributing to projects with unfamiliar tech stacks, and building tools (like my four-tool framework itself) rather than just fixing bugs. Each scenario will refine how I think about structured contribution work.
