# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

ElvisValcarcel

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53#issuecomment-5907781151

I'd like to take this issue (#53). Running `python -m pytest tests/unit/test_pii_scrubber.py -v --runxfail` (Windows 10, Python 3.13.14, commit f89c06f), four of the five xfailed tests fail because `(555) 123-4567` is left unscrubbed as described. The fifth, `test_mixed_pii_and_text`, fails for a different reason. Next I'll post the full reproduction with commands and output.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53#issuecomment-5908829417

### Reproduction

**Environment:** 
- Windows 10, Python 3.13.14, pytest 9.1.1, structlog 26.1.0 
- commit f89c06f
- using fresh venv with only `pip install pytest structlog` _not the full make setup_

**Steps to reproduce:**
```
# setup environment
git clone https://github.com/codepath/pathreview-ai301-fa26-s1.git
cd pathreview-ai301-fa26-s1
py -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install pytest structlog

# start tests
python -m pytest tests/unit/test_pii_scrubber.py -v # baseline test

python -m pytest tests/unit/test_pii_scrubber.py -v --runxfail # ignoring xfail markers, verbose

python -m pytest tests/unit/test_pii_scrubber.py --runxfail --tb=line -q # ignoring xfail markers, summary

```
**Observed:** 
- baseline `20 passed, 5 xfailed`. 
- with `--runxfail`, `5 failed, 20 passed`.
- Four failures are the parenthesized format left untouched:

*Excerpt from running `python -m pytest tests/unit/test_pii_scrubber.py --runxfail --tb=line -q` for a summary*
```
=================================================================================================== short test summary info ===================================================================================================
FAILED tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_us_phone_number_redaction - AssertionError: assert '[REDACTED]' in 'Call me at (555) 123-4567'
FAILED tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_us_phone_formats - AssertionError: assert '[REDACTED]' in 'Contact: (555) 123-4567'
FAILED tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_detect_phone_pii - assert 0 > 0
FAILED tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_phone_at_start_of_text - AssertionError: assert '[REDACTED]' in '(555) 123-4567 is my phone number.'
FAILED tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_mixed_pii_and_text - assert 'Python' in "\n        Professional Background:\n        I worked at TechCorp for [REDACTED]ications.\n        Email: [REDACTED]\n        Phone: [REDACTED]\n        SSN: [REDACTED]\n        I'm skilled in AWS and...
5 failed, 20 passed in 0.13s
```

**Note: `test_mixed_pii_and_text`** is the fifth xfail for #53, but it has no parenthesized number. Its `555-123-4567` is redacted as intended, and fails because `Python` is removed from the text: `I worked at TechCorp for [REDACTED]ications.`. This appears to be a separate, over redaction rather than the parenthesized phone bug.



## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Two runs were made, with the first not being officially logged, but being 20/20. Below is the saved 18/20 log:

categories: clear-accept 6/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4
agreement: 18/20 scored items  (bar: 18/20: PASS)

**Package analysis**

*Excerpt from `eval-run.txt`*
```
item    gold    verdict  agree  note
pkg-01  accept  reject   NO     failed: input-validation
pkg-02  reject  reject   yes    
pkg-03  accept  reject   NO     failed: ai-disclosure, honest-artifacts
```

ID: pkg-03
Rubric decision: reject, failing ai-disclosure and honest-artifacts
Gold label: accept
Why my rubric read it that way: 

*Exact quote from pkg-03*
- contribution policy (CONTRIBUTING.md section "Use of AI", AI_POLICY.md): AI-assisted coding is welcome with a human in the loop who understands the work; comments to maintainers must be written by humans in their own words, and AI-generated comments may be hidden

pkg-03 doesn't require disclosure, but it failed on `ai-disclosure` and `honest-artifacts`. I believe that the reason for `ai-disclosure` to fail is similar to the tradeoffs section that I detail later in this report. There is ambiguity in what is a human comment and when AI-assisted coding contributions are allowed in the repo. As for how `honest-artifacts` failed, I am not entirely sure but I would guess it has something to do with the "visible artifact in the repo" portion of the check, which may have counted as behavior being unchanged on 15.2.0 as a certainty claim.


**Check rationale**


| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| ai-disclosure |The AI policy in the repo-facts block, read against the reproduction report and claim comment. | If there is an AI policy that requires AI disclosure, comments disclose it openly. If there isn't a policy or the policy doesn't require disclosure: pass. Treat every package as AI-assisted. | required |

Initially, Ai-disclosure didn't exist until I got near the end of defining my first set of checks. I decided to go back to my unit-1 rubric for inspiration and it reminded me how important having an AI-disclosure check is. One draft included an incorrect phrasing of "If there isn't a policy or a policy **require** disclosure, pass" which was missing the word "doesn't" right inbetween "policy" and "require", which I caught right before I ran my agreement score for my claim. I deliberately added "Treat every package as AI-assisted" to prevent the grader from arbitrarily deciding is pkg-20 comments had nothing to disclose.



**Trade-offs**

In my run, I believe my inclusion of "Treat every package as AI-assisted" caused the pkg-03 miss since the repo accepts a human comment due to ambiguity. I would've re-ran again but I decided to settle with the 18/20 to not struggle against two conflicting edgecases. Generally speaking, I think treating every package as AI-assisted is a good, if not very sophisticated, approach to the amount of AI comments that flood github.

As I mentioned earlier, my first run was actually 20/20 (and unfortunately I forgot to log it). Nevertheless, pkg-01 agreed in run 1, but failed `input-validation` in run 2 (18/20) despite both versions keeping this check in particular unmodified. It seems as if there is no discernable reason beyond potentially variance in the model's reasoning or the check is somewhat ambiguous to allow the variance to begin with.


---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
