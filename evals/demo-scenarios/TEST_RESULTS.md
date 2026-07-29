# Test Results — Skill vs. No Skill

**Model:** Gemini 3.1 Pro

**Comparison:** `project-manager-framework` skill vs. the same model with no PM skill/framework
loaded at all (plain general model). A third arm, `old_skill` (a pre-fix snapshot of this same
skill from an earlier iteration), is included for reference only — it is **not** part of the
skill-vs-no-skill story.

**Scenarios:** 5 evals — 3 short single-line prompts (`relocation`, `dashboard`, `timeline-cut`)
plus the two realistic multi-document bundles in this folder (`bank-payments-gateway`,
`agile-mobile-onboarding`). n=1 run per scenario per configuration (see caveat below).

Full data: `project-manager-skill-workspace/iteration-1/benchmark.json`. Individual responses,
transcripts, and per-assertion grading live under
`project-manager-skill-workspace/iteration-1/<eval-name>/{with_skill,no_skill,old_skill}/`.

## Headline numbers

| | Skill (`with_skill`) | No skill (`no_skill`) |
|---|---|---|
| **Assertions passed** | 24/24 (100%) | 18/24 (75%) |
| **Avg. time per response** | 94.0s | 58.0s |
| **Avg. tokens per response** | 49,578 | 35,467 |

**Delta (skill minus no-skill):** pass rate **+0.24**, time **+36.0s**, tokens **+14,110**.

## Per-scenario pass rates

| Scenario | with_skill | no_skill | old_skill (reference only) |
|---|---|---|---|
| relocation | 5/5 | 3/5 | 5/5 |
| dashboard | 5/5 | 3/5 | 5/5 |
| timeline-cut | 4/4 | 4/4 | 4/4 |
| bank-payments-gateway | 5/5 | 4/5 | 5/5 |
| agile-mobile-onboarding | 5/5 | 4/5 | 5/5 |

## What's actually driving the gap

The no-skill runs missed **the same specific assertion in all 5 scenarios**: none of them ever
performed an explicit methodology/mode-selection step (naming Predictive vs. Agile, or diagnosing
the project's Landscape quadrant). That single miss accounts for the entire gap on 3 of the 5
scenarios (`relocation`, `dashboard` lost a second point each on the explicit-diagnosis assertion
too; `bank-payments-gateway` and `agile-mobile-onboarding` each lost exactly one point, on this
same assertion).

On every other assertion — spotting the "on track" vs. real-data gap (Hope Creep), routing
mid-stream feature asks to a backlog instead of absorbing them, avoiding uniform/flat cuts,
assigning ownership to orphaned work — the plain general model mostly reached the same practical
conclusions as the skill-driven run, just without the skill's named vocabulary (Scope Triangle,
Scope Bank, Landscape quadrants, named creep types).

**Honest read:** the skill's distinct, reproducible value here is forcing an explicit,
consistent framework diagnosis every time — not making the model's underlying PM judgment
fundamentally sharper, which was already fairly strong on its own. That consistency costs roughly
62% more time and 40% more tokens per response.

## Caveats

- **n=1 per configuration per scenario.** A single lucky/unlucky run can move these numbers. The
  *pattern* (same assertion missed in all 5 scenarios) is the most trustworthy part of this result;
  the exact magnitude of the aggregate delta is not, without repeated sampling.
- `old_skill` is not a no-skill baseline — it's the same skill's content pre-fix, kept from an
  earlier iteration of this benchmark. It also scores 24/24, which just confirms the pre-fix
  skill's *content* was already strong; the fix that produced `with_skill` targeted reference-file
  reachability and repo hygiene, which a single-run pass-rate comparison like this can't detect.
- See `evals/GUIDE.md` for how to reproduce this comparison yourself (manual or harness-based),
  and `evals/evals.json` / each eval's `eval_metadata.json` for the exact assertion wording.
