# GitHub community experiment: 27 October–10 November 2026

This is an operational experiment, not a prediction of follower growth. Day 0 is 27 October; day 7 is 3 November; day 14 is 10 November. Dates use Europe/London time.

## Objective

Make public research software easier to discover, try and discuss, and make the relationship between the projects and their maintainer clear. The primary visibility outcome is the observed change in personal followers, when a verified baseline and endpoint are available. Supporting outcomes are first-run reports, distinct external participants and actionable contributions. Report Stars and Forks separately; neither proves installation or sustained use.

## Executed launch work — 27 October

| Work | Verified state |
|---|---|
| Add project, research-note and participation entry points to the profile | Published in [0215bdf](https://github.com/ZipengWu365/ZipengWu365/commit/0215bdfb492daf5b854c3cf1b31e7dd5b652ac54); previous full profile preserved unchanged in RESEARCH_PROFILE.md |
| Publish an English note and Chinese counterpart on context-compression evaluation | Published in [notes/](../notes/README.md); illustrative example, no new benchmark result claimed |
| Improve the existing TOMC first-run thread | Updated [issue #11](https://github.com/ZipengWu365/TOMC/issues/11); no duplicate thread created |
| Add TOMC community/follow entry points | English/Chinese README additions and issue chooser merged through [PR #21](https://github.com/ZipengWu365/TOMC/pull/21), commit 09954ee31aaa96455cc123aabd2334d527378751 |
| Keep release inventory consistent | TOMC's own manifest generator and --check passed in the [documentation workflow](https://github.com/ZipengWu365/TOMC/actions/runs/40541082544); source code, packages and existing traffic workflow were not changed |
| Enable TOMC Discussions | Not completed: settings/discussion-creation operations are absent from the current connector; [categories and opening posts](discussions-launch.md) prepared |
| Establish follower and project baseline | [First API snapshot](metrics/2026-10-27.json): 5 personal followers; TOMC 265 Stars, 25 Forks, 28 subscribers at 16:22:33 UTC |
| Collect daily aggregate metrics | Workflow installed and [first run verified](https://github.com/ZipengWu365/ZipengWu365/actions/runs/40540271783); collection guarded to 27 October–10 November |
| Schedule day-7/day-14 reviews | Two review runs configured for 3 and 10 November, London evening; final run is instructed to remove the metrics cron trigger |
| Contribute to external repositories | Not yet submitted; inspect contribution rules and a concrete issue before posting |
| Turn TimeInfra into a public forum | Deferred until the intended public repository and publication boundary are verified; no private research copied |

The document workflow checks establish successful documentation changes and hash-inventory consistency. They do not establish a full TOMC test-suite pass, a working client integration, a benchmark improvement or follower growth.

## Remaining checkpoints

| Window | Work to perform | Evidence to keep |
|---|---|---|
| Days 1–3: 28–30 October | Inspect first-run feedback; reproduce a concrete reported problem before changing instructions | Environment, reproduction, correction or explicit inability to reproduce |
| Days 4–6: 31 October–2 November | Inspect 2–3 relevant external issues; contribute only where a verified answer or tested change is available | Issue/PR URL, contribution rules, evidence and submitted/draft state |
| Day 7: 3 November | Compare available metrics; find the main onboarding problem | Verified counts, distinct participants, failures and missing measurements |
| Days 8–10: 4–6 November | Prepare a second evidence-backed research note from existing public work | Sources, runnable example if available, validation and disclosure boundary |
| Days 11–13: 7–9 November | Follow up on substantive questions and contributions; avoid repeating unanswered promotion | Resolution, merged/declined contribution or unanswered status |
| Day 14: 10 November | Review outcomes, stop the experiment's scheduled collector and choose continue, revise or stop | Observed changes, confounders, outstanding support work and next experiment |

Planned work is not completed work or an assertion that every intermediate task is automated. The configured automation covers daily aggregate measurements and the two review checkpoints. Future public replies require reading the actual thread and the repository's contribution rules. Do not fabricate tests, mass-comment, participate in reciprocal-follow schemes or automate endorsements. Do not publish unpublished theory, private repositories or health data as marketing material.

## Cadence and workload

Use one bounded community review per week and short responses when a real report needs attention. Reuse the same first-run feedback entry point. Do not create multiple daily promotional posts or interrupt research with continuous counter checking. No advertising spend is part of this experiment.

## Interpretation

Record followers, Stars, Forks, aggregate repository traffic when accessible, distinct external participants and concrete task outcomes. A missing value stays missing; the first available follower snapshot starts the measurable follower interval. Do not infer past follower counts or divide new followers by repository visitors and label it a profile-conversion rate. Repository traffic does not identify who visited the personal profile.

Before/after differences describe observed changes. They do not isolate causality from other posts, launches, advertising, seasonality or platform recommendations. Small samples support diagnosis, not a reliable forecast of a large audience.

[Metric definitions and baseline](metrics/README.md) · [Discussion setup pack](discussions-launch.md)
