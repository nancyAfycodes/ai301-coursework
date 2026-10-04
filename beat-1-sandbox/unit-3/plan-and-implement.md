# Unit 3 — Plan and Implementation

## GitHub Username
nancyAfycodes

## Plan Comment

**Link:** https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-5952027615

---

## Branch
fix/71-heading-fixture-indent

## Pull Request
**Link:** https://github.com/codepath/pathreview-ai301-fa26-s3/pull/86

---

## Test Evidence

### Before (Bug reproduced)
```
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy FAILED [ 66%]

_________________________ TestReadmeParser.test_extract_heading_hierarchy _________________________

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

    assert len(headings) > 0

```

### After (Fix implemented and tested)
```
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [ 66%]

================================== 14 passed, 1 xfailed in 0.40s ==================================

```
---

## Eval Iterations

**Run history:**
- Run 1: 14/20 (initial rubric — "Steps are executable" and "Test plan is concrete" too strict)
- Run 2: 18/20 (generalized checks, added "Thread conventions" check) ✓ PASS

**Package analysis:**
In Run 1, the rubric was rejecting good plans (pkg-02, pkg-05, pkg-08, pkg-09) because "Steps are executable" and "Test plan is concrete" were written too specifically for issue #71. By generalizing the pass conditions to look for "concrete actions a stranger could follow" instead of "exact line numbers and file paths," the rubric caught more true positives. The second iteration also added a "Thread conventions" check to catch plans that violated communication norms (like pkg-20).

**Check rationale:**
"Steps are executable" checks whether the plan's implementation steps describe concrete actions that someone could actually follow. This is important, for vague or incomplete steps can make a plan being unable to be built. Generalization helps in versions help in working for any rather than specific issues.

**Trade-offs:**
The rubric focues on generalizations rather than specificity to avoid false rejections. This means some plans with unusual but valid approaches might still disagree with gold labels, but it stops rejecting perfectly good plans. Furthermore, I'd add sub-checks for different complexity levels (e.g., one-line fix vs. multi-file refactor).
