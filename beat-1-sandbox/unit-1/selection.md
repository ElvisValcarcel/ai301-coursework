# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53

**Verdict output**

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

````
**Mode:** live · **Scope check:** all three candidates are in `codepath/pathreview-ai301-fa26-s1` — inside the scoped source. Path Review house rule applied: other students' claim comments do not block an issue.

### Accepted, in fit order

**1. #53 — PII scrubber fails to redact parenthesized US phone numbers.** Best fit: a self-contained regex fix in `safety/pii_scrubber.py` with four named failing tests, the smallest and most bounded of the three, and the only one nobody has commented on. AI-adjacent without being AI-shaped work.

**2. #68 — Keyword search raises `ZeroDivisionError` when the index is empty.** RAG-layer backend logic, which the profile calls out as interesting. The issue names both files, states the cause, and estimates 2–4 hours; the fix direction is unambiguous.

**3. #62 — Health check references `settings.redis_host`.** An API route fix, named explicitly in the profile, but it ranks last because the issue leaves a design fork open — add `redis_host`/`redis_port` to `Settings`, or rebuild the client from `redis_url` — and the profile prefers decisions already settled.

*Rejected:* none.

*Tension worth noting:* on #62 the claimant self-identifies as a course TF rather than a student, and the house rule names students. `is_available_issue` still passes on the rubric's own terms (`assignee count of 0`, no linked PR), but it's the weakest availability of the three.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53",
    "checks": [
      {"name": "active_repo", "grade": "pass",
       "evidence": "Newest default-branch commit 2026-09-16T21:42:18Z by Andrew Burke; 7 days before today, inside the 90-day window; repo not archived."},
      {"name": "allows_ai_contribution", "grade": "pass",
       "evidence": "docs/CONTRIBUTING.md states no AI ban and no invite-only access: 'Browse issues and find one that interests you.' No AI_POLICY.md or equivalent exists."},
      {"name": "well_scoped", "grade": "pass",
       "evidence": "Maintainer-filed bounded bug naming pii_scrubber.py, a runnable repro with observed output, and four failing tests in tests/unit/test_pii_scrubber.py."},
      {"name": "is_available_issue", "grade": "pass",
       "evidence": "state OPEN, assignees: [], zero comments; no open PR linked (only open PR #74 targets issue #60; the lone 'referenced' event is commit 8d0c24b in the separate repo Evin009/ai301-coursework)."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68",
    "checks": [
      {"name": "active_repo", "grade": "pass",
       "evidence": "Same repo: newest default-branch commit 2026-09-16T21:42:18Z, 7 days before today; not archived."},
      {"name": "allows_ai_contribution", "grade": "pass",
       "evidence": "docs/CONTRIBUTING.md carries no AI ban and no invite-only access."},
      {"name": "well_scoped", "grade": "pass",
       "evidence": "Maintainer-filed: names rag/retriever/keyword_search.py and tests/unit/test_keyword_search.py, the cause (BM25Okapi divides by corpus_size), the xfail marker to remove, and 'Estimated effort: 2-4 hours'."},
      {"name": "is_available_issue", "grade": "pass",
       "evidence": "state OPEN, assignees: [], no linked or open PR; two claim comments by yulijasso (author_association NONE) on 2026-09-20, which the scope.md Path Review house rule says do not block."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62",
    "checks": [
      {"name": "active_repo", "grade": "pass",
       "evidence": "Same repo: newest default-branch commit 2026-09-16T21:42:18Z, 7 days before today; not archived."},
      {"name": "allows_ai_contribution", "grade": "pass",
       "evidence": "docs/CONTRIBUTING.md carries no AI ban and no invite-only access."},
      {"name": "well_scoped", "grade": "pass",
       "evidence": "Maintainer-filed: names api/routes/health.py and core/config.py, the defect (Settings has redis_url, not redis_host/redis_port), and repro steps (GET /health returns 503 with an AttributeError in the log)."},
      {"name": "is_available_issue", "grade": "pass",
       "evidence": "state OPEN, assignees: [], no linked or open PR; two claim comments by ZJShown (author_association NONE) on 2026-09-21, which the scope.md Path Review house rule says do not block."}
    ],
    "verdict": "accept"
  }
]
```
````

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

Fourteen full runs were made, in this order:
`19/20`, `19/20`, `20/20`, `19/20`, `19/20`, `17/20`, `17/20`, `18/20`, `17/20`, `18/20`, `19/20`, `17/20`, `18/20`, `19/20`

The last score recorded (matching `eval-run.txt`) was the following agreement line:

```
agreement: 19/20 scored items  (bar: 18/20: PASS)
```

A short note: the `20/20` on run 3 was from a rubric I didn't keep and later edits were made to cover more average cases since
there was a sense of non-determinism to many of the individual runs since runs 12, 13, and 14 failed on different items every time
despite using the same rubric.

**Issue analysis**

`issue-04`: My rubric rejected this issue, while the gold label accepted it, and this was the only disagreement on my final run for 19/20 (recorded in `eval-run.txt`)

```
issue-04  accept  reject   NO     failed: well_scoped
```

3/4 of the required checks passed on it from my rubric, and it was the well_scoped one that rejected it.
This was because the entire issue body is in one line, which violates it's passing condition of "No vague, one line issues."

Otherwise, it matched all other criteria like having a good first issue tag, which fit the "maintainer filed bounded bug documentation" in the same condition. Since in the same passing condition there was a vagueness, the "reject if any required check fails, is missing, or the verdict is otherwise unclear" portion of my rubric's verdict directy led to a rejection of the issue when it should've been accepted.

**Check rationale**

The `well_scoped` check from `rubric.md` quoted as written:
| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
|well_scoped| repo-facts or issue body | No vague, one line issues that are wishcasting for a future feature, has to be well defined, or include maintainer filed bounded bug documentation | required |

The reasoning behind this form would be to prevent vague, nonspecific issues that would be unbounded. The "or include maintainer filed bounded bug documentation" at the end was inspired by the `evidence-guide.md`'s advice of "Short is not the same as unscoped" and "grade the size of the work being asked for, not the polish of the writeup". One line is fine, but a vague one liner that is nonspecific should get instantly filtered.

**Trade-offs**

The trade off of this is that it can be overly strict (which I am fine with). Unfortunately, due to the fact of undeterministic answers from LLMs, sometimes it focuses too much on the exclusionary part of the pass condition, specifically, line count and vagueness, and doesn't properly weigh the bounded bug conditional at the end. Because of this, `issue-04`'s "a genuinely small, well-understood bug that a maintainer wrote down in one line" was wrongfully rejected seven out of the fourteen times I ran my rubric against the issues.

The final run shows the cost is contained to this category rather than a widespread issue across the *issues*:
```
categories: claimed 4/4  clear-accept 7/8  dead-repo 3/3  policy 1/1  scope 4/4
```

Since the miss was in `clear-accept` and not `scope`, the check is still doing it's job for unscoped issues, but as a consequence over rejects instances such as this. Tightening up the language to place the vagueness/one-line nature would risk allowing large or unbounded scope issues so I decided to leave it strict and keep my score at 19/20. Luckily, this strictness works well with the Path Review #53, which passed due to it's maintainer-filed nature.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.


**Selection rationale**

**1. Fit to my interests and to the time available.**

I'm generally interested in well defined small to medium backend problems in Python, and completely disinterested in CSS/HTML or open ended refactoring since I understand that can get messy quickly. #53 is very manageable, essentially a regex pattern in `safety/pii_scrubber.py` that matches numbers like `555-123-4567` but not `(555) 123-4567`. I have experience with regex and I can see how this is both a low hanging fruit and important since PII scrubbing is make or break. Also, it already names four tests that have to pass so it's well bounded rather than me having to guess the definition of done.

**2. What the verdict identified correctly, and what I weighed that it could not.**

The verdict cleanly picked an issue that wasn't claimed, while at the same time it didn't really weigh on how much it would teach me, nor did it catch some things like pytest forbidding the test to not pass through xpass since the maintainers know it's currently broken and temporarily disabled the test.

**3. Anticipated difficulty in claiming it.** 

I don't expect claiming it will be difficult, no assignees, comments, and the house rules dont block me from claiming issues that people commented on anyway. The PR I open is really all that matters so regardless of someone commenting before me or not, I continue. Getting all of the CI's to turn green is going to be hard as well as remembering to remove the xfail. I may also need to wait for a maintainer to release the approval for the workflows to run.

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
