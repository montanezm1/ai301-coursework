# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/62

**Verdict output**

```
Scope check: all three candidates are in codepath/pathreview-ai301-fa26-s3, the scoped repo. No claim comments present on any of them, so the Path Review house rule doesn't come into play here.

Rubric checks executed (from rubric.md): Unclaimed, Maintainer alive, Repo in use, Scope fits, AI contribution allowed (all required), Newcomer signal (preferred).

Issue #62 — Health check references `settings.redis_host`, which does not exist on Settings
- Unclaimed: pass — assignees: none; no linked/mentioned PR; 0 comments
- Maintainer alive: pass — human commit by Aburke225 on 2026-09-16, 5 days before today (2026-09-21), well within 90 days
- Repo in use: pass — archived: false; last push 2026-09-16, 5 days ago, within 180 days
- Scope fits: pass — one bounded bug in one file (api/routes/health.py): use settings.redis_url instead of the nonexistent redis_host/redis_port; concrete repro steps given (GET /health → 503, AttributeError in log)
- AI contribution allowed: pass — no CONTRIBUTING.md, PR template, or README statement on AI use anywhere in the repo; silence passes
- Newcomer signal (preferred): pass — good first issue label
Verdict: accept

Issue #72 — `verify_password` raises `UnknownHashError` on malformed stored hashes instead of returning False
- Unclaimed: pass — assignees: none; no linked/mentioned PR; 0 comments
- Maintainer alive: pass — same recent human commit, 5 days before today
- Repo in use: pass — same as above
- Scope fits: pass — one bounded bug in one function in core/security.py; one named covering test (tests/unit/test_security.py, manifest id H-05) to un-xfail; effort estimate 1-2 hours
- AI contribution allowed: pass — silent policy
- Newcomer signal (preferred): pass — good first issue label
Verdict: accept

Issue #73 — README and `.env.example` disagree about which LLM API key to set
- Unclaimed: pass — assignees: none; no linked/mentioned PR; 0 comments
- Maintainer alive: pass — same recent human commit
- Repo in use: pass — same as above
- Scope fits: pass — one bounded doc/config-consistency fix touching two named files (README.md, .env.example); effort estimate 1-2 hours
- AI contribution allowed: pass — silent policy
- Newcomer signal (preferred): pass — good first issue label
Verdict: accept

Ranked read-out (fit profile: Python/JS/Git/web-dev experience; wants to build debugging and testing skill; prefers small bounded bug/doc tasks within a week; avoids large architecture, infra, or math):
1. #62 — a genuine runtime bug with a concrete repro (GET /health → 503, AttributeError in the log), in a small FastAPI route. Best match for "improve debugging" — you reproduce a real failure, trace it to the wrong attribute name, and fix it.
2. #72 — also a real logic bug with a clear test to un-xfail, but requires a little more unfamiliar-library context (passlib's exception hierarchy) before the fix is obvious.
3. #73 — valid and bounded, but it's a documentation/config-sync task with no code logic or test involved, so it exercises debugging/testing the least of the three.
```

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/62",
    "checks": [
      {"name": "Unclaimed", "grade": "pass", "evidence": "assignees: none; no linked or mentioned PR; 0 comments"},
      {"name": "Maintainer alive", "grade": "pass", "evidence": "human commit by Aburke225 on 2026-09-16, 5 days before today (2026-09-21)"},
      {"name": "Repo in use", "grade": "pass", "evidence": "archived: false; last push 2026-09-16, 5 days before today"},
      {"name": "Scope fits", "grade": "pass", "evidence": "one bounded bug in api/routes/health.py (use settings.redis_url instead of nonexistent redis_host/redis_port), with a concrete repro: GET /health returns 503 with an AttributeError in the log"},
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "no CONTRIBUTING.md, PR template, or README statement on AI use anywhere in the repo"},
      {"name": "Newcomer signal", "grade": "pass", "evidence": "labels include good first issue"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
    "checks": [
      {"name": "Unclaimed", "grade": "pass", "evidence": "assignees: none; no linked or mentioned PR; 0 comments"},
      {"name": "Maintainer alive", "grade": "pass", "evidence": "human commit by Aburke225 on 2026-09-16, 5 days before today"},
      {"name": "Repo in use", "grade": "pass", "evidence": "archived: false; last push 2026-09-16, 5 days before today"},
      {"name": "Scope fits", "grade": "pass", "evidence": "one bounded bug in core/security.py (verify_password should catch UnknownHashError and return False), one named covering test (manifest id H-05) to un-xfail, estimated 1-2 hours"},
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "no CONTRIBUTING.md, PR template, or README statement on AI use anywhere in the repo"},
      {"name": "Newcomer signal", "grade": "pass", "evidence": "labels include good first issue"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
    "checks": [
      {"name": "Unclaimed", "grade": "pass", "evidence": "assignees: none; no linked or mentioned PR; 0 comments"},
      {"name": "Maintainer alive", "grade": "pass", "evidence": "human commit by Aburke225 on 2026-09-16, 5 days before today"},
      {"name": "Repo in use", "grade": "pass", "evidence": "archived: false; last push 2026-09-16, 5 days before today"},
      {"name": "Scope fits", "grade": "pass", "evidence": "one bounded doc/config consistency fix across two named files (README.md, .env.example), estimated 1-2 hours"},
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "no CONTRIBUTING.md, PR template, or README statement on AI use anywhere in the repo"},
      {"name": "Newcomer signal", "grade": "pass", "evidence": "labels include good first issue"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

**Run history**

1. Full 20-item run, initial rubric (`Scope fits` v1): `agreement: 17/20 scored items  (bar: 18/20: below the bar)`; `categories: claimed 4/4  clear-accept 6/8  dead-repo 3/3  policy 1/1  scope 3/4`. Disagreements: issue-01, issue-15, issue-19, all traced to the `Scope fits` check.
2. `--only issue-01,issue-15,issue-19,issue-05,issue-10,issue-20,issue-09` after the first `Scope fits` revision (added the linked-PR/age signal): `agreement: 5/7 scored items`. issue-15, issue-09, issue-05, issue-10, issue-20 corrected; issue-01 and issue-19 still disagreed.
3. `--only issue-01,issue-15,issue-19,issue-05,issue-10,issue-20,issue-09` after the second `Scope fits` revision (clarified that multi-file/multi-cause asks toward one outcome are not umbrellas): `agreement: 7/7 scored items`. All seven canaries agreed.
4. Full 20-item confirming run with `--save-run`: `agreement: 20/20 scored items  (bar: 18/20: PASS)`; `categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 4/4`. This is the run recorded in `eval-run.txt`.

**Issue analysis**

issue-19 (source `zxcalc/zxlive#517`, category `clear-accept`). My rubric's verdict: `accept`. Gold verdict: `accept`. The issue is a maintainer-filed UI freeze bug: the collaborator names two possible root causes ("The matchers are slow for certain rewrites" and "UI update is waiting for the matching thread to finish") plus three "Additional suggestions" (multi-processing, selective category matching, a separate apply-thread). Under the first rubric draft, `Scope fits` failed this issue, with the model's own evidence reading "Body lists two separate potential root causes plus three additional suggested improvements... rather than one bounded fix." After I revised the check to state explicitly that a maintainer's list of candidate causes and optional follow-on improvements for one bug is still one bounded outcome, the same evidence produced a pass: one symptom (the freeze), one filer, no invitation to split the work across contributors. `Unclaimed` (no assignee, no linked PR, no comments), `Maintainer alive` (human commit the day before capture), `Repo in use` (active, unarchived), and `AI contribution allowed` (silent policy) all passed independently of the rubric change, so the verdict flipped from `reject` to `accept` — matching gold.

**Check rationale**

Quoted from `rubric.md`, `Scope fits` row, pass condition (current wording): "Pass when the issue's ask amounts to one bounded outcome (a single feature, a single bug fix, or a single documentation topic) that one contributor could deliver in one pull request — even when it lists several files to touch, several sub-steps, or several candidate causes or approaches toward that one outcome."

I chose this wording because the first full eval run showed that a naive reading of "bounded contribution" made the grader conflate "touches more than one file or names more than one possible cause" with "is an umbrella issue," rejecting two genuine gold-accept issues (issue-01's multi-file docs task, issue-19's multi-cause bug diagnosis) while a stricter check was still needed to keep failing real umbrellas (issue-05's open-ended incremental-typing effort, issue-10's literal 100-item megaissue list). The threshold I settled on — "could one contributor deliver this in one pull request" — is deliberately behavioral rather than adjectival: it asks whether the ask collapses into a single diff, not whether the writeup merely lists several things, which is a condition a grader can apply consistently across both kinds of issue.

**Trade-offs**

This exact wording change is what flipped issue-19 (and issue-01) from `reject` to `accept` between eval run 1 and the confirming `--only` re-runs (runs 2-3 in the run history above), so it's a check whose result I can point to a changed issue for. What it gives up: by instructing the grader not to fail an issue just because it lists several causes or optional follow-on improvements, the check is now less able to catch a case where those "additional suggestions" are not actually optional — where properly fixing the bug would require touching multiple subsystems (in issue-19's case, both the matcher algorithm and the threading model) rather than picking one. A stricter check would flag that as too large for a first PR; mine accepts it as one bounded fix. I accept that limitation because the alternative, stricter wording rejected two of the three `scope`-category disagreements in the first full run on issues gold actually marked `accept`, which is an expensive miss on a 20-item graded eval, and it would likely have also rejected good bounded live candidates the moment they named more than one relevant file — which #62, #72, and #73 all do.

---

## Selection rationale

**Selection rationale**

I picked #62 because it's a small, clear-cut runtime bug — a one-file fix with a concrete repro (`GET /health` → 503), which fits within my one-week time limit and lets me practice debugging a real failure instead of just editing documentation.

The rubric correctly identified that #62 is unclaimed, in an active repo, allows AI-assisted contributions, and is a single bounded fix — every required check passed on solid evidence. Beyond what the rubric measures, I weighed that the issue's repro steps (a `GET /health` call) let me verify my own fix locally before opening a PR, which mattered to me as a way to build confidence working in a codebase I don't know yet.

I expect claiming and completing this issue to be low difficulty: locating the health-check route, swapping the `redis_host`/`redis_port` reference for `redis_url`, and removing the matching `xfail` marker (and its `pyproject.toml` suppression) should be quick. The main risk I anticipate is CI — the repo requires all five jobs (lint, typecheck, test-unit, test-integration, frontend) to pass, so I'll need to be careful to confirm the removed suppression doesn't leave anything else behind.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
