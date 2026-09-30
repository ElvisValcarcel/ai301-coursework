# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

- Where it lives: The Environment line of the candidate reproduction report, the version the issue targets is in the issue section and the thread highlights and latest release line of Repo facts. Live: the issue thread and the draft reproduction steps.
- What good looks like: basic information like operating system and tool/programming versions are recorded and if there is any difference between what the issue targets and the environment, it will be stated in the report.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

- Where it lives: the steps list of the candidate reproduction report and any repos, configs, or files these steps depend on. The trigger to compare it against is in the issue section.
- What good looks like: A stranger can run every step from public code: commands and input are the issue's trigger OR the change is explained.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

- Where it lives: the output blocks and the actual line of the reproduction report, read against what the issue section states actually happens.
- What good looks like: the artifact shows the behavior the issue reports, not a similar one: if the behavior isn't reproducable, it passes only if the report shows the attempt's output and explicitly names what differs.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

- Where it lives: the claim comments assertions ("the cause is...", "confirmed", "without a doubt", "guaranteed", etc) and the report conclusion compared against the report's shown artifacts.
- What good looks like: Regardless of certainty, confidence, cause, or confirmation, claims must point to a shown artifact.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

- Where it lives: the prospective claim comment read against the Issue and the contribution policy of repo facts read against both comments. Live: CONTRIBUTING.md or AI_POLICY.md and the draft files
- What good looks like: the claim lists specific next steps for the issue without giving a deadline, generic boilerplate, or +1s. AI disclosure, if required, will be disclosed. If not required, pass. Treat every package as AI-assisted.