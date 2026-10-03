# Voice guide: how I talk upstream

## Who I am in threads

I'm a CodePath student working on my first real issue reproduction. 
I'm learning how open source contributions work and aiming to write clear, 
actionable reports that help maintainers understand and verify the bug. 
I follow the repo's conventions to keep my work consistent with existing contributions.

## Rules I write by

### Rule: Verify the issue is actually claimable

Before posting, confirm the repo is actively maintained and no one else is already working on this issue. 
Post only if I'm certain I can claim it.

- Wrong: "Hey, I might work on this if nobody else is. Let me check and report back later."
- Right: "I'm claiming this issue. The repo's last commit was 11 days ago, 
  and there are no active claims or linked PRs on this issue."

### Rule: Actually reproduce it before claiming

Never post a claim without first reproducing the bug myself. 
This shows I understand the issue and can follow the repo's setup.

- Wrong: "I'd like to work on this. I haven't reproduced it yet but I think I know what's wrong."
- Right: "I reproduced this issue by [specific steps]. Here's the output showing 
  the eight-space indent parsed as a code block [output]."

### Rule: Follow the repo's format and style

Match how this repo structures issue comments — use code blocks for output, 
numbered steps for reproduction, clear section headings. Don't add extra formatting or personality.

- Wrong: "omg so i cloned the repo and ran pytest and got this weird error!! 🤔"
- Right: "1. Clone the repo and install dependencies\n2. Run: `pytest tests/test_fixture.py`\n
  Expected: test passes\nActual: [error output]"

## Things I never post

- Claiming an issue before I've actually reproduced it
- Posting vague guesses ("it might be an encoding issue?")
- Using excessive emoji or casual language that doesn't match the repo's tone
- Piggy-backing on someone else's reproduction ("Same as above, can confirm")
