# Contribution: Explorer settings duplicate app settings, only Explorer's copy used

Path: `beat-2-contribution/contribution-story.md`

**Contribution Number:** [1]

**Student:** [Nancy Anatuanya]

**GitHub Username:** [nancyAfycodes]

**Issue:** **Issue:** https://github.com/code-charity/youtube/issues/4348

**Pull Request:** [GitHub PR link, once opened]

---

## Toolkit

**Unit 5: Issue scout with human-activity checks and per-repo ranking limits**

I built a skill that searches GitHub for issues by profile (Python debugging, larger codebases), ranks results by activity and author, and grades them with a three-check rubric. Four scans plus two grading batches (13 issues total, ~$3 cost) revealed that “Repo is active” passed on bot commits alone, that fresh issues clustered in one repo without per-repo limits, and that the rubric’s “Scope feasible” row had no written pass condition. I fixed these by checking for human commits only, adding per-repo limits to keep results diverse, and writing the real scope condition into the rubric table. Final pick: code-charity/youtube#4348 (JavaScript browser extension), accepted by the rubric and unclaimed—a language trade-off made because it was the only unclaimed issue passing all checks after grading 13 candidates.

**Unit 6: Voice guard with Upstream rules and repo memory file**
I built a voice guard that checks my claim and other upstream posts against rules before it goes onto GitHub, and a memory file (CLAUDE.local.md) that teaches Claude about the youtube repo structure so orientation doesn’t repeat. The hook initially failed because the settings template used python3 instead of python on Windows and $HOME didn’t expand correctly, but when I manually checked with --draft, it worked. The scope files were also limited to the classroom repo, so I updated them with the “wild” versions to support real-world issues. I missed this step originally, which is why it failed. Next, I added an Upstream section to my voice guide with three subsections (claims, questions, pings), each with guide rules on when to post and how to show one's work. I also patched my rubric’s scope check to accept issues with open edges and flag them with difficulty notes (straightforward/moderate/ambitious) instead of rejecting them, which let me claim youtube#4348 even though “playlists” and “block where” weren’t fully specified.

**Unit 7: [one line on the tool work]**

[2-4 sentences: fill in Unit 7]

**Unit 8: [one line on the tool work]**

[2-4 sentences: fill in Unit 8]

---

## Why I Chose This Issue
I ran my issue-scout skill from Unit 5 to find a real-world issue matching my profile. Scan 1 accepted 5 issues, but all were recently posted by repo owners. Grading Batch 1 rejected all 5 picks from the Issue Selection site: they were all claimed. Grading Batch 2 accepted one: code-charity/youtube#4348 (block playlists), which I immediately claimed.

My scout graded it as accept with difficulty ambitious — the feature request leaves scope open (“my mix, podcasts, etc.” and where to hide them?), which means raising those questions with the maintainer early, and asking clarifying questions. The repo is JavaScript (Python preference was my preference), however, I've always wanted to practice and improve my skills in JavaScript, so I'm using this course project as practice.

I chose this over waiting for a Python issue because it’s unclaimed, the maintainer is responsive (commits daily), and I have a clear first step: trace how the existing blocklist code works and understand where playlist filtering fits. The issue description is sparse, so asking good questions upfront matters. On closer inspection, I noticed that contributing.md page has details that will help me in completing the project, since it has a link, and it's reflected in my claim comment.

My scout worked, it filtered out claimed issues and caught the difficulty edge, rubric’s original scope check was too strict, rejecting most real-world issues. I patched it in Unit 6 to flag open edges instead of rejecting them. The comment filter never worked (all issues were hours old with 0 comments), so the per-repo limit saved me from five duplicates of the same issue.

**Claim comment:** https://github.com/code-charity/youtube/issues/4348#issuecomment-6721980800

---
