# Unit 2 — Reproduction and Claim

## Claim Comment

**Link:** https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-5858619495

**Text:**
I'm claiming this issue and have already reproduced the bug.

**Issue:** Issue #71 — The heading hierarchy test fixture has an 8-space indentation 
that's being parsed as a code block instead of test content, causing the test to fail.

**Repo status:** The repo is actively maintained — last commit was on 2026-09-16, 11 days ago. 
There are no active claims or linked PRs on this issue.

**Reproduction:** Successfully reproduced the bug by running the test with `--runxfail`. 
The 8-space indentation breaks Markdown parsing, causing heading extraction to return an 
empty list.

**Next:** I will fix the indentation in the test fixture and remove the @pytest.mark.xfail 
marker (manifest H-04).

---

## Reproduction Comment

**Link:** https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71#issuecomment-5860714611

**Text:**
## Issue #71 Reproduction Report

### Environment
- Python: 3.14.6
- pytest: 9.1.1
- OS: Windows 11
- Repo: pathreview-ai301-fa26-s3

### Steps to Reproduce
1. Clone the fork of pathreview-ai301-fa26-s3
2. Create and activate virtual environment: `python -m venv venv && source venv/Scripts/activate`
3. Install dependencies: `pip install -e .`
4. Run the test with --runxfail flag: `python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail`

### Result
The test fails outright under --runxfail

### Behavior Shown
```
assert len(headings) > 0
E assert 0 > 0
E + where 0 = len([])

tests/unit/test_readme_parser.py:156: AssertionError
```

The parser returns an empty list because the markdown's 8-space indentation is parsed as a code block.

### Conclusion
Successfully reproduced issue #71. The 8-space indentation in the test fixture causes Markdown to parse it as a code block, breaking the heading extraction. Fix: remove indentation from fixture and remove `@pytest.mark.xfail` marker (manifest H-04).

---

## Eval Iterations

**Run history:**
- Run 1: 12/20 (original rubric)
- Run 2: 14/20 (with encoding fix)
- Run 3: 15/20 (consistent with encoding fix)

**Issue analysis:**

pkg-16 (wrong-target): My rubric decided accepted it, even though the gold label was to reject. Reason being that the package showed a concrete error in the output section ("Behavior shown" check passed). However, the error was unrelated to the fixture indentation issue. The rubric's "Behavior matches issue" check was too loose; it only required "a concrete error," not the specific indentation-caused error that issue #71 illustrates.

**Check rationale:**

"Behavior shown — Output shows the indent-as-code-block parsing problem: a fixture with eight-space indentation is parsed as a code block, causing the heading hierarchy test to fail". Therefore, I wrote this check to be very specific to issue #71 because distinguishing between "any error in output", and "the specific 8-space indent error" is important in reproducing the issue as well as its related fix.

**Trade-offs:**

The specificity of "Behavior shown" means some legitimate reproductions that show related but slightly different indent-parsing errors may be rejected. For instance, a report showing 8-space indent breaking a different parser (not heading extraction) would fail. Therefore, I'd like to add a secondary check: "Indent-related parsing failure" (preferred weight) to  account for variations without having to reject the issue.
