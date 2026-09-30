# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
|env-recorded  | Reproduction report's environment record compared against the versions in the issue body and thread target |OS and tool versions are recorded, any version difference from what the issue targets will state the difference in the report |required |
|input-validation |Command and input in the reproduction report steps compared against the trigger in the issue body if present |Commands and input are the issue's trigger, or any change is stated with a reason | required |
|behavior-matched |Output excerpts in reproduction report compared against the actual behavior in the issue reports if present |The artifact reproduces behavior the issue describes or the report says it could not reproduce and shows the attempts output, naming what differed |required |
| ai-disclosure |The AI policy in the repo-facts block, read against the reproduction report and claim comment. | If there is an AI policy that requires AI disclosure, comments disclose it openly. If there isn't a policy or the policy doesn't require disclosure: pass. Treat every package as AI-assisted. | required |
| rerunnable-steps |steps in the reproduction report, including any repos they depend on, configs, or files | every step can be run from public code and the stated starting state | required |
| honest-artifacts | the reports stated conclusions read against its own shown artifacts | every claim of cause, certainty, or confirmation is backed by a visible artifact in the repo | required |
| claiming-comment |The claim comment read against the issue | specified intent and next step for this specific issue without providing a timeline, boilerplate text that can be applied to any issue, or just a +1 | required |

## Verdict rule

Ready iff every required check passes. Any fail, or unclear counts as a hold. Preferred checks never change the verdict
