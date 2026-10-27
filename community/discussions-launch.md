# TOMC Discussions launch pack

Prepared 27 October 2026. **Status: setup material; Discussions has not been enabled by this change.**

The current connected tools can edit repository content and issues, but do not expose the repository-setting or discussion-creation operations. An administrator can enable Discussions in TOMC's **Settings → General → Features → Discussions**. Follow the [official quickstart](https://docs.github.com/en/discussions/quickstart).

Use one TOMC forum first. Do not open multiple empty forums or publish private TimeInfra implementation details to populate a community.

## Suggested initial categories

| Category | Format | Scope |
|---|---|---|
| Announcements | Announcement | Releases and documented changes |
| Q&A | Question/answer | Installation, configuration and interpretation |
| Show and tell | Open-ended | Reproducible examples and evaluations, including failures |
| Ideas | Open-ended | Concrete use cases and proposed integrations |

## Opening post 1 — welcome

**Title:** Start here: try TOMC, compare evidence, report what broke

Welcome to the TOMC community. Start with the [first-run guide](https://github.com/ZipengWu365/TOMC#first-run-tomc): save a synthetic task note, open a fresh chat using the same local notebook, and check the returned evidence after recall.

Questions, failed installations and reproducible negative results are welcome. For the existing first-run exercise, continue using [issue #11](https://github.com/ZipengWu365/TOMC/issues/11), so reports stay together. Distinct bugs belong in their own issue; open-ended questions belong in Q&A.

Please include versions and configuration, and keep private conversations, credentials and notebook databases out of public posts. TOMC is research software. A tool appearing in a client does not establish end-to-end compatibility or prove that native model requests use it.

## Opening post 2 — evaluation question

**Title:** Which constraint disappears first when you reduce a context budget?

The [context-compression checklist](https://github.com/ZipengWu365/ZipengWu365/blob/main/notes/2026-10-27-context-compression-checklist.md) starts from an intentionally small synthetic history: a proposed API rename is cancelled, one task is complete, and another remains unfinished.

For your own shareable example, what must survive for the next task to be correct? Include the history, expected facts, method/version, budget and actual output. A short counterexample is more actionable than an unsupported success percentage. This question does not assume TOMC passes the example.

## Opening post 3 — integration evidence

**Title:** What counts as a working assistant integration?

Please separate configuration written, tools discovered, a successful tool call, context actually used by the reader, and a verified task result. Report the assistant/version and TOMC/version for every stage tested; mark the rest as untested.

Do not infer request interception from an MCP installation alone. Existing [host integration documentation](https://github.com/ZipengWu365/TOMC/blob/main/docs/host_integration_validation_20261022.md) describes its own test scope. A minimal synthetic reproduction is enough to begin a useful discussion.

## After enabling

Publish the welcome post, configure the four categories, and add the verified Discussions URL to the community entry page. Do not label the draft posts as published until their live URLs have been checked. Preserve issue #11 and any existing replies rather than duplicating or deleting them.
