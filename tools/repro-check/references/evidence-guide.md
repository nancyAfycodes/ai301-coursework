# Evidence guide: where proof lives in a reproduction package

## Environment

Where it lives: The repro report's "Environment" or "Setup" section, listing Python version, 
test framework version, and which files are involved in the test.

What good looks like: The report names the exact Python version used, the test framework 
(pytest, unittest, etc.), and identifies the test file path. For issue #71, it should 
mention the fixture file and the test that reads it.

## Repo is active
Where it lives: repo-facts block (GitHub API: pushed_at timestamp)

## Steps

Where it lives: The repro report's "Reproduction Steps" section, numbered and sequential.

What good looks like: A stranger can follow the steps without reading the issue description. 
Each step is a concrete action with exact commands shown. Steps should clearly show how to 
trigger the issue that's being reproduced.

## Behavior shown

Where it lives: The repro report's "Output" or "Error" section, with command output or error messages pasted verbatim.

What good looks like: The artifact (error message, test output) directly shows the issue named in #71 
— that an eight-space indent is being parsed as a code block instead of test content. 
It's not a different error; it's this specific defect.

## Honesty

Where it lives: The repro report's "Result" or "Conclusion" section, and the claim comment's promise.

What good looks like: The report states clearly: "I reproduced this issue" with evidence, 
or "I could not reproduce it, here's what I found instead." The claim comment promises work 
without claiming success beforehand. No speculation presented as fact.

## Comms

Where it lives: The claim comment and repro report text, checked against the Path Review repo's contribution style.

What good looks like: Language is specific and plain. Code blocks are used for output, 
numbered lists for steps. The tone matches the repo (professional, clear, no excessive emoji or casual language). 
The claim comment names the issue and what you'll do next; the repro report shows what you found.
