# Contribution: Explorer settings duplicate app settings, only Explorer's copy used

Path: `beat-2-contribution/contribution-story.md`

**Contribution Number:** [1]

**Student:** [Nancy Anatuanya]

**GitHub Username:** [nancyAfycodes]

**Issue:** https://github.com/earthobservations/wetterdienst/issues/3878

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

I ran 4 scans with my issue-scout skill to find a real-world issue that matched my profile. 
Scan 1 locked to the classroom repo and surfaced high-comment issues, exposing a scope 
mismatch — I fixed the queries to expand to GitHub's public repos. Scan 2 found 
rockcarver/frodo-cli#1088 (secret headers leak), a perfect match, but it was completed 
and merged before I could claim it. Scan 3 revealed that the tier-2 query pointed back 
to the sandbox, so I dropped it. Scan 4 returned earthobservations/wetterdienst#3878: 
a settings-duplication bug in an active 456-star multilingual app (gutzbenj is actively 
triaging today). The issue fits perfectly — TypeScript/Vue work builds my JavaScript 
skills that I'll like to improve upon, the repository is large and well-maintained, 
and the maintainer has laid out exact steps to fix it. The scout's verdict was accept, 
and I'll use this as a first step in contributing to open source. 

**Claim comment:** https://github.com/earthobservations/wetterdienst/issues/3878#comment-[your-comment-id]
(Posted 2026-11-07 at 13:32)

**Toolkit**

- Tool: issue-scout (4 scans with refined search strategy and rubric)
- What it produced: Filtered 299+ GitHub issues through Python/JavaScript language matching, bug labels, and comment-count ranking; graded top 5 with rubric checks (repo active, manageable scope, not already claimed)
- Difficulties: Tier-2 label only exists in classroom repos (sandbox); bot commits can fool "active repo" check; 5-comment cutoff barely filtered anything; Python/JavaScript filters required language:python syntax (not --language flag)
- What changed: Dropped tier-2 query, fixed language filter syntax, tightened future criteria to check for human maintainers vs. bot-only commits

---
