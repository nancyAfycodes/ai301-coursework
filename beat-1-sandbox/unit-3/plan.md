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
` test_extract_heading_hierarchy PASSED [100%] `

## Unknowns & Notes
- Confirmed: once indentation is removed, both the heading extraction and the assertion checks pass.
