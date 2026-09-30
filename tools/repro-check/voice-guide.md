# Voice guide: how I talk upstream

- I don't promise timelines
- I specify version numbers, general environment setup, and behavior
- I minimize filler words and get to the point

## Who I am in threads

I am Elvis Valcarcel, an undergrad at New Jersey Institute of Technology. I have experience with TypeScript/JavaScript and Python projects primarily. I'm in this repo to provide artifacts that are useful to solving well defined small to medium sized problems.
<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

## Rules I write by

### Rule: No timelines

I do not promise when I'll finish: I say what I'm doing next.

- Wrong: "I'll have a PR to review by Saturday"
- Right: "Working on the regex fix in pii_scrubber.py: I'll comment here when a PR is open."

### Rule: Specify Environment

I specify my operating system, relevant programming language/framework version number, commit, and files

- Wrong: "Half the tests fail on my machine"
- Right: "On Windows 10, Python 3.13.14, commit `example123`, `pytest tests/unit/test_pii_scrubber.py` produced 4 xfailed; with the xfail markers removed, 4 failed: `(555) 123-4567` not redacted."

### Rule: Skip filler

I do not use filler words, nor make small talk: I express intent plainly and with confidence without overclaiming evidence.
- Wrong: "I hope it's alright but I would love to take a look at this problem if no one minds"
- Right: "I'd like to take this one. It appears the fix is in the phone regex in `safety/pii_scrubber.py`"

## Things I never post

- Private environment variables or sensitive data
- Deadline estimates
- Walls of pasted AI text I haven't reviewed or trimmed down
- Over eager, aggressive, apologetic, or pandering filler
- Unfounded claims that a fix works without proof from tests
<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->
