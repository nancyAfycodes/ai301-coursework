# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`
---

## Pull request

**Pull request**

## Summary
This PR fixes issue #71 by removing the 8-space indentation from the test fixture 
in `test_extract_heading_hierarchy`. The indentation caused the Markdown to parse 
the fixture content as a code block, resulting in the heading hierarchy parser 
returning an empty list instead of extracting headings.

## Issue
Closes #71

## Changes made
- Removed 8-space indentation from the markdown fixture string in `test_extract_heading_hierarchy`
- Removed the `@pytest.mark.xfail` decorator (lines 134-137)
- Test fixture now correctly parses heading hierarchy

## Testing
- [x] **CI is green on this PR (all five jobs)** — required for review (all passed: frontend, lint, test-integration, test-unit, typecheck)
- [x] Unit tests pass (`make test-unit`)
- [x] Integration tests pass (`make test-integration`)
- [x] Linter passes (`make lint`)
- [x] Type checker passes (`make typecheck`)
- [ ] New/updated tests cover the changes
- [x] If this fixes a seeded bug: removed its `@pytest.mark.xfail` marker (removed at lines 134-137)

### Before (Bug reproduced)
``` 
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy FAILED [ 66%] 
```
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

E assert 0 > 0
E + where 0 = len([])

tests/unit/test_readme_parser.py:152: AssertionError
===================================== short test summary info =====================================
FAILED tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy - assert 0 > 0
============================= 1 failed, 13 passed, 1 xfailed in 0.49s ============================ 


### After (Fix verified)
======================================= test session starts =======================================
platform win32 -- Python 3.14.6, pytest-9.1.1, pluggy-1.6.0 -- E:\CodePath\AI 301\pathreview-ai301-fa26-s3\venv\Scripts\python.exe
cachedir: .pytest_cache
rootdir: E:\CodePath\AI 301\pathreview-ai301-fa26-s3
configfile: pyproject.toml
plugins: anyio-4.15.1
collected 15 items

```
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_standard_readme XFAIL (is...) [ 6%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_longer_than_10000_chars PASSED [ 13%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_with_code_blocks PASSED [ 20%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_without_code_blocks PASSED [ 26%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_empty_readme PASSED [ 33%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_with_only_whitespace PASSED [ 40%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_bytes_input PASSED [ 46%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_bytes_with_utf8 PASSED [ 53%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_invalid_content_type PASSED [ 60%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [ 66%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy_no_headings PASSED [ 73%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_with_badges PASSED [ 80%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_readme_without_badges PASSED [ 86%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_metadata_structure PASSED [ 93%]
tests/unit/test_readme_parser.py::TestReadmeParser::test_word_count_accuracy PASSED [100%]
```
================================== 14 passed, 1 xfailed in 0.72s ==================================

The `1 xfailed` is from a different test (test_parse_standard_readme at line 18), not this fix.

Verified locally:
```bash
python -m pytest tests/unit/test_readme_parser.py -v
# Result: 14 passed, 1 xfailed
```

## Screenshots / Demo
N/A

## Notes for Reviewers
The root cause was that Python multi-line strings preserve indentation from the source code. 
By removing the leading spaces from the fixture lines, the Markdown parser can now correctly 
identify and extract the heading hierarchy.


**Link:** https://github.com/codepath/pathreview-ai301-fa26-s3/pull/86


## Branch

**Branch**
fix/71-heading-fixture-indent

## Eval iterations

**Run history**
- Run 1: 20/20 (perfect agreement across all categories) ✓ PASS

**Package analysis**

pkg-02 (clear-accept): gold=accept, verdict=accept. Your rubric accepted it because 
the PR description shows concrete before/after test evidence, the diff matches the plan scope, 
and all template sections are completed. This is why it deserves acceptance.

**Check rationale**

"Test evidence shown | PR description's testing/evidence section | PR shows concrete 
before/after output (or logs, or screenshots) that proves the fix works. The evidence 
matches what the plan said to verify."

I wrote this check to ensure PRs prove their fixes actually work. Without evidence, 
a maintainer can't verify the change does what it claims.

**Trade-offs**

The rubric accepts any format of evidence (pytest output, logs, screenshots, CI status) 
as long as it's observable and matches the plan. This means unusual verification methods 
get accepted, but it prevents false rejections of valid approaches.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
