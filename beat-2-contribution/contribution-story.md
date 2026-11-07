# Contribution: Explorer settings duplicate app settings, only Explorer's copy used

Path: `beat-2-contribution/contribution-story.md`

**Contribution Number:** [1]

**Student:** [Nancy Anatuanya]

**GitHub Username:** [nancyAfycodes]

**Issue:** **Issue:** https://github.com/samcorky/menagerist/issues/294

**Pull Request:** [GitHub PR link, once opened]

---

## Toolkit

**Unit 5: Issue scout with Python/JavaScript language filtering and real-world search**

I built a skill that searches GitHub for open-source issues matching my profile: 
Python debugging with JavaScript stretching, in larger codebases. Ran 4 scans ( about $4 in total cost), 
discovering that gh requires language:python in the query string (not --language flags), 
that course labels like tier-2 point back to the sandbox, and that bot commits can fool 
the "active repo" check. Each scan refined the strategy: removing repo lock, fixing 
language filtering, dropping the tier-2 query. Scan 4 found earthobservations/wetterdienst#3878: 
a real settings-duplication bug in an active 456-star multilingual app (TypeScript/Vue). 
The task is clear, the maintainer is responsive, and it's perfect practice for me to practice using JavaScript

**Unit 6: [one line on the tool work]**

[2-4 sentences: fill in Unit 6]

**Unit 7: [one line on the tool work]**

[2-4 sentences: fill in Unit 7]

**Unit 8: [one line on the tool work]**

[2-4 sentences: fill in Unit 8]

---

## Why I Chose This Issue

I ran 5 scans with my issue-scout skill to find a real-world issue that matched my profile. 
Scan 1 locked to the classroom repo and surfaced high-comment issues, exposing a scope 
mismatch, I, then, fixed the queries to expand to GitHub's public repos. Scan 2 found 
rockcarver/frodo-cli#1088 (secret headers leak), a perfect match, but it was completed 
and merged before I could claim it. Scan 3 revealed that the tier-2 query pointed back 
to the sandbox, so I dropped it. Scan 4 returned earthobservations/wetterdienst#3878: 
a settings-duplication bug in an active 456-star multilingual app. Scan 5 focused on 
Python only and returned both #3878 and samcorky/menagerist#294. 

I chose #294 because it's pure Python debugging with a smaller, focused scope—exactly 
what I need for a first contribution. The issue has clear repro steps and an identified 
likely cause (lru_cache engine outliving asyncio.run loops), so the path to fix is clear. 
Both issues was graded as "accept" by my rubric, but #294 is better suited for a first 
contribution. I'll tackle #3878 (settings refactor, TypeScript/Vue) as a second contribution 
once #294 is merged, which is a great stretch goal for building JavaScript skills that I'm interested in developing further.

**Claim comment:** https://github.com/samcorky/menagerist/issues/294#issuecomment-6713725471

**Toolkit**

- Tool: issue-scout (5 scans with refined search strategy and rubric, plus grading)
- What it produced: Filtered 296+ Python issues through bug label matching and comment-count ranking; graded top candidates with rubric checks; both finalists passed (menagerist#294 and wetterdienst#3878)
- Difficulties: Python-only focus eliminated JavaScript options; owner-opened issues risk being fixed by maintainer; comment filter barely worked (all 0 comments); rubric too loose to distinguish beginner-friendly from complex refactors
- What changed: Removed JavaScript queries for Python focus; decided to grade BEFORE claiming (caught that #3878 scope was too large); deferred #3878 as second contribution for later

---
