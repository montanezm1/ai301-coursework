# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Unclaimed | The repo-facts block fields `this issue: assignees` and `linked PRs`, plus the issue comment thread for claim statements or mentioned PRs. | Pass when there is no current assignee, no open linked or mentioned PR, and no unresolved statement that someone is currently working on the issue. Closed unmerged PRs and comments that clearly withdraw or release a claim do not count as active claims. | required |
| Maintainer alive | The repo-facts block fields `last 5 default-branch commits` and `maintainer first-response sample`, plus issue comments whose `author_association` is Owner, Member, or Collaborator. | Pass when at least one non-bot human committed to the default branch within 90 days of the bundle capture date, or a maintainer responded to an issue within 30 days. A bot-authored commit alone does not pass. | required |
| Repo in use | The repo-facts block fields `archived`, `latest release`, and `last push to any branch`. | Pass when `archived` is false and either the latest release is within 365 days or the last push is within 180 days of the bundle capture date. | required |
| Scope fits | The issue body and comment thread, plus the repo-facts `this issue: linked PRs` field. | Pass when the issue's ask amounts to one bounded outcome (a single feature, a single bug fix, or a single documentation topic) that one contributor could deliver in one pull request — even when it lists several files to touch, several sub-steps, or several candidate causes or approaches toward that one outcome. Do not fail a check just because it names multiple files or multiple possible causes: a single author's own multi-file feature, or a maintainer's list of candidate causes and optional follow-on improvements for one bug, is still one outcome. Fail only when the evidence shows the work is actually meant to be split across separate contributors or separate PRs — a list of unrelated linked issues to pick from, an open invitation for many different people to each take a different unrelated piece, or explicit maintainer language inviting that split — or when it is a change requiring core internals, a pure usage or support question, an unresolved design or product decision that blocks implementation (whether still being debated in comments or left open in the issue itself, such as an unspecified asset, format, or approach), or an issue that has stayed open for years through two or more closed-unmerged linked PRs without resolving. A terse report, missing reproduction steps, or lack of an acceptance-criteria checklist does not fail this check by itself. | required |
| AI contribution allowed | The repo-facts block `contribution policy` line. | Pass unless the policy explicitly bans AI-assisted or AI-generated contributions. Disclosure, testing, personal-understanding, and human-review requirements pass. A missing or silent policy passes. | required |
| Newcomer signal | The issue labels, issue body, and comments by an Owner, Member, or Collaborator. | Pass when the issue has a `good first issue` or equivalent newcomer label, or a maintainer explicitly says the work suits a first-time contributor. | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept only when every required check passes. A `fail` or `unclear` grade on any required check rejects the issue. Preferred checks never change the verdict; they only help rank accepted issues.
