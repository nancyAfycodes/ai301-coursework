# Unit 3 — Plan and Implementation

## GitHub Username
nancyAfycodes

## Plan Comment

**Link:** https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-5952027615


# Implementation Plan for Issue #71

Branch: fix/71-heading-fixture-indent

## Root Cause
The test fixture in `tests/unit/test_readme_parser.py::test_extract_heading_hierarchy` 
has 8-space indentation at the beginning of each line. This indentation causes Markdown 
to parse the text as a code block instead of regular content. The `_extract_heading_hierarchy` 
parser returns an empty list because it finds no headings in a code block.

**Evidence:** Reproduced in unit 2 — the test output shows `assert 0 > 0` (empty heading list) 
when running with `--runxfail`.

## Scope
This fix changes only:
- The test fixture indentation in `tests/unit/test_readme_parser.py` (remove leading spaces)
- The `@pytest.mark.xfail` marker that marks the test as expected-to-fail (remove it)

No changes to the parser code, no refactoring, no additional tests.

## Implementation Steps
1. Open `tests/unit/test_readme_parser.py`
2. Locate `test_extract_heading_hierarchy` method (around line 138)
3. Remove the 8-space indentation from the markdown fixture string (lines 141-152)
4. Remove the decorator block at lines 134-137 (`@pytest.mark.xfail(strict=True, reason="issue #71...")`)
5. Save the file

## Testing & Verification
Run the test to verify the fix:
```bash
cd pathreview-ai301-fa26-s3
source venv/Scripts/activate
python -m pytest tests/unit/test_readme_parser.py -v
```

Expected result: Test passes (no XFAIL, no failures). Output should show:
`test_extract_heading_hierarchy PASSED [100%]`

## Unknowns & Notes
- Confirmed: once indentation is removed, both the heading extraction and the assertion checks pass.

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
