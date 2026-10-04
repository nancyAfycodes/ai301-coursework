# Unit 3 — Plan and Implementation

## GitHub Username
nancyAfycodes

## Plan Comment

**Link:** https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-5952027615

**Text**

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
` test_extract_heading_hierarchy PASSED [100%] `

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
- Run 1: 18/20 (initial generalization fixes)
- Run 2: 17/20 (test plan check split, evidence guide generalized)
- Run 3: 19/20 (loosened "Scope is bounded" and "Steps are executable") ✓ PASS

**Package analysis:**
pkg-20 (thread-convention): gold=reject, verdict=accept. Your rubric accepts it because 
the thread-convention checks are too permissive. This is a known edge case — the checks 
successfully catch most violations but miss this particular combination.

**Check rationale:**
"Steps are executable | Plan describes how to make the change in understandable terms; 
someone could start attempting it" — This generalization accepts different levels of detail (step-by-step vs. high-level) as long as the plan is actionable.

**Trade-offs:**
The rubric prioritizes accepting reasonable plans over strict formatting. This means some unusual but valid approaches get accepted, but it prevents false rejections.
