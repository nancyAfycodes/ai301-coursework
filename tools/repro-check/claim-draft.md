I'm claiming this issue and have already reproduced the bug.

**Issue:** Issue #71 — The heading hierarchy test fixture has an 8-space indentation 
that's being parsed as a code block instead of test content, causing the test to fail.

**Repo status:** **Repo status:** The repo is actively maintained — last commit was on 2026-09-16, 11 days ago. There are no active claims or linked PRs on this issue.

**Reproduction:** Successfully reproduced the bug by running the test with `--runxfail`. 
The 8-space indentation breaks Markdown parsing, causing heading extraction to return an 
empty list.

**Next:** I will fix the indentation in the test fixture and remove the @pytest.mark.xfail 
marker (manifest H-04).