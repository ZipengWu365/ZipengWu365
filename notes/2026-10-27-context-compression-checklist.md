# Your prompt got smaller. Did your agent get worse?

Zipeng Wu · 27 October 2026 · Evaluation note

[中文](2026-10-27-context-compression-checklist.zh.md) · [All notes](README.md)

A context-compression result needs two answers: how much input was removed, and whether the next task still succeeds. A token count answers the first question. It cannot, by itself, answer the second.

## A small example worth testing

Consider this **invented history**, written only to illustrate an evaluation case:

```text
09:00 — Rename /v1/orders to /v2/orders during the refactor.
09:10 — Cancel that rename. External clients still depend on /v1/orders.
09:20 — The cache cleanup is finished. Pagination tests are still missing.
Next task — Write a handoff for another developer.
```

Before running any model, define what a correct handoff must preserve:

| Requirement | Pass condition |
|---|---|
| Latest decision | Keep /v1/orders unchanged; identify the rename as cancelled. |
| Unfinished work | List pagination tests as still missing. |
| Completed work | Do not list cache cleanup as unfinished. |
| Evidence | Make it possible to trace the decisions back to the supplied history. |

A compressed history that retains the proposed rename but drops its cancellation has lost a task-critical distinction. A fluent handoff can still be wrong. This is a logical example, **not a measured failure of TOMC or another tool**. Passing it would establish only that this case worked under the tested setup.

## Compare the request you actually send

For a first comparison, hold the task, reader model and version, instructions, tools and evaluation rubric fixed. Compare full history, a simple recent-history baseline, and the candidate preparation method. Report whether every baseline fits the reader's context limit. Do not silently truncate an overflowing baseline and describe it as full history.

Keep system instructions and tool-call/result relationships intact. Count the prepared history separately from the complete outgoing request. Include any preparation instructions or wrappers that the reader also receives. State the tokenizer and whether counts come from local tokenization or provider-reported usage.

Start with one inspectable case. Then test multiple original or shareable histories containing changed decisions, negation, unfinished work and irrelevant detail. Report the number of tasks and repeat runs. An anecdote is useful for debugging; a general performance claim needs a wider evaluation.

## Keep four measurements separate

| Measurement | What to record | What it does not establish alone |
|---|---|---|
| Context size | Original and prepared history; total outgoing input | Correct decisions or completed tasks |
| Task quality | Predefined pass/fail checks; failure examples; evaluator | Reliability outside the tested cases |
| Latency | Preparation and end-to-end time; repeated runs | The same speedup on other systems |
| Cost | Actual usage and billing rules, cached input, output and retries | Energy use or carbon savings |

For an unchanged measurement convention, history-token reduction can be reported as `1 - prepared_history_tokens / original_history_tokens`, when the denominator is positive. Label it **history-token reduction**. Do not relabel that ratio as a billing reduction or end-to-end efficiency gain.

When caching applies, compare like-for-like cache conditions and report them. Do not infer the invoice from the uncached input list price alone. An extra retry can also change the result. Without usage or billing evidence, leave cost as unmeasured.

## Where TOMC fits

[TOMC Memory](https://github.com/ZipengWu365/TOMC) provides CPU context preparation and explicit task-note tools. Its current public documentation distinguishes a Python integration that supplies prepared context from a host that owns its native chat and compaction. Installing an MCP tool alone does not prove that every model request passes through it. Consult the [context-ownership policy](https://github.com/ZipengWu365/TOMC/blob/main/docs/context_ownership.md) and the current [first-run guide](https://github.com/ZipengWu365/TOMC#first-run-tomc).

A note saved with `remember_memory` and recovered with `recall_memory` in a new chat is a useful installation check. It is not a compression benchmark. Current recording behavior also depends on runtime version and settings; read the storage notes before supplying sensitive material.

The repository's [recorded results](https://github.com/ZipengWu365/TOMC#measured-savings) belong to their documented protocols. This article adds no measured savings, universal compatibility claim or environmental estimate.

## A report that someone else can use

Copy this into a report, using synthetic or otherwise shareable data:

```text
Tool version/commit:
OS and integration route:
Reader model/version and settings:
Task and history:
Required constraints and expected output:
Baselines and context-limit handling:
Budget and tokenizer:
Original/prepared history tokens:
Complete request input and provider usage:
Task checks passed/failed, including failed examples:
Preparation/end-to-end time and repeat count:
Cache conditions and actual cost, or "not measured":
Smallest reproducible example:
```

For a first TOMC trial, [use the existing first-run feedback thread](https://github.com/ZipengWu365/TOMC/issues/11). A blocked installation or a failed recall is useful evidence too. Keep keys, personal conversations and notebook databases out of public reports.

The first question after compression should be concrete: **which decision, constraint or unfinished task can the next assistant still recover?**
