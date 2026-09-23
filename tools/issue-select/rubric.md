# Rubric: is this a good first issue?
## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
|active_repo|Most recent commit timestamp in repo-facts|A commit was made within the last 90 days, or repo-facts indicates maintainer engagement is active|required|
|allows_ai_contribution| Contribution policy text in repo-facts| Does not explicitly ban AI generated code, contributions, or require invite only access | required |
|well_scoped| repo-facts or issue body | No vague, one line issues that are wishcasting for a future feature, has to be well defined, or include maintainer filed bounded bug documentation | required |
|is_available_issue| Assignees list, linked PRs in issue body or issue events, and comment thread | The issue is currently open, has active comments seeking an assignee, with assignee count of 0, no open PRs associated with it, or no comment within the last 14 days claiming the work | required |


## Verdict rule
Verdicts are binary: accept if every required check passes, reject if any required check fails, is missing, or the verdict is otherwise unclear. Preferred checks (pass or fail) do not affect the outcomes of verdicts whatsoever: they are used soley for ranking purposes separately from the verdict.
