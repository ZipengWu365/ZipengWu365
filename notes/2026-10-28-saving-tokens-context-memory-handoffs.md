# Saving Tokens: 13 Tools for Context Compression, Memory, and AI Handoffs

**By Zipeng Wu · 28 October 2026**

*Scope: a selected, non-exhaustive roundup based on primary project documentation checked on 28 October 2026. This is a guide to capabilities and trade-offs, not a controlled performance comparison of all thirteen projects.*

You are halfway through a project. The next chat needs the background again. You switch from Claude Code to Codex, or bring the work into WorkBuddy, and find yourself explaining which constraints still apply, which plan was cancelled, and which tests have never actually run.

**You switched AI assistants. Somehow, you are the one doing the onboarding again.**

Searching for ways to save tokens brings up several different kinds of tools: prompt compressors, terminal-output filters, code-navigation tools, persistent memory systems, and ways to carry work between assistants.

Before installing another layer, identify the problem you actually have. Are requests too large? Are important facts hard to retrieve? Or does changing assistants mean explaining the project from scratch?

This article maps the tools, provides a practical handoff template, and explains what to check before trusting a token-saving claim.

*Disclosure: I maintain TOMC Memory, one of the projects covered below. I use the same capability-based categories for other projects and state the conditions and limitations of the measurements involving my own project.*

## 1. Which part of the workflow needs attention?

I would start with these five questions. This is a selection framework, not a ranking.

| Problem | Approach to investigate | What to check |
|---|---|---|
| A long document contains only a small amount of task-relevant material. | Prompt or context compression. | Could omitted information change the next answer or action? |
| Terminal commands, tests, and logs produce repetitive output. | Tool-output filtering. | Are error locations, important warnings, and failure causes preserved? |
| The assistant reads entire files to understand a small part of the code. | Symbol-level retrieval and targeted reads. | Can it obtain the definitions, references, and dependencies it needs? |
| New sessions repeatedly ask for the same facts and project conventions. | Persistent memory and retrieval. | What is stored, when is it updated, and how are incorrect memories corrected? |
| Switching between Claude Code, Codex, or WorkBuddy requires another project briefing. | Portable working notes and handoff materials. | Can the latest decisions, unfinished work, evidence, and verification steps travel with the task? |

One tool may address several rows. Still, memory support, smaller inputs, and lower bills are separate claims. Evidence for one does not establish the others.

## 2. Thirteen projects and project families

The table groups projects by what their documentation says they do. It does not rank them by stars or their largest advertised saving. Inclusion does not mean I installed and tested every integration.

| Project or family | Documented focus | A reason to investigate it |
|---|---|---|
| **LLMLingua / LongLLMLingua / LLMLingua-2** | Model-assisted prompt compression that selects which text or tokens to retain.[^lingua] | You already have long inputs and want to evaluate compression methods. |
| **RTK, open-source edition** | Filters and reformats development-command output to reduce redundant text.[^rtk] | Logs and command output account for a substantial part of your context. |
| **Serena** | Retrieves and edits code at the symbol level, reducing the need to read complete files.[^serena] | Your coding assistant needs more targeted access to a codebase. |
| **TOON** | A compact serialization of JSON data with lossless round-trips.[^toon] | Structured data dominates your input. Measure with your actual data and tokenizer. |
| **Headroom** | Compresses tool outputs and other context; offers proxy and MCP integrations, retrieval of cached originals, and cross-agent memory.[^headroom] | You need both input management and continuity across assistants. |
| **claude-mem** | Captures observations from agent work, creates summaries, and retrieves context in later sessions. Its documentation lists support for multiple assistants.[^claudemem] | You want to reduce manual work in maintaining cross-session records. |
| **Mem0** | Persistent memory, fact extraction, and retrieval for applications. Its documented basic configuration uses an LLM.[^mem0] | You are adding a general-purpose memory layer to your own application. |
| **Graphiti** | Temporal graphs of facts and relationships, including validity windows and links to source episodes.[^graphiti] | Facts change over time, and you need relationship queries and provenance. |
| **Hindsight** | Retain, recall, and reflect operations, supported by several retrieval strategies and coding-agent integrations.[^hindsight] | You need to accumulate, retrieve, and synthesize experience across sessions. |
| **MemOS** | Memory storage, retrieval, and management, including a local plugin, viewer, and cross-task reuse.[^memos] | You need inspectable local memory and want to assess its supported agent integrations. |
| **OpenViking** | Organizes knowledge, memory, and skills through a filesystem-style context database with layered loading.[^openviking] | You want a hierarchical way to organize and inspect an agent's context. |
| **Letta / Letta Code** | A stateful agent environment; Letta Code supports self-editable memory and Git-tracked context.[^letta] | You are open to adopting a broader agent runtime. |
| **TOMC Memory** | Task-oriented context preparation on local CPU, without auxiliary neural inference in the core path, plus explicit note storage, recall, and handoff materials.[^tomc-main][^tomc-method] | You already have a preferred assistant and want to manage inputs and carry working notes between sessions or tools. |

Check editions as well as names. For example, RTK distinguishes the Apache-2.0-only `rtk-oss` build from distributions containing BUSL-1.1 components. Their licensing scope differs.[^rtk]

Local compression, cross-agent memory, inspectable records, and Git-managed context already appear in this ecosystem. To understand meaningful differences, compare integration effort, update semantics, recovery from mistakes, and performance on actual tasks.[^headroom][^claudemem][^memos][^letta]

## 3. How to choose without installing an unnecessary layer

**For a small set of stable conventions, start with native project instructions.** Claude Code's `CLAUDE.md` and Codex's `AGENTS.md` provide native routes. Claude Code also documents conditions under which it reads `AGENTS.md`. Check the loading rules and scope for your installed version.[^claude-native][^codex-native]

**When code and logs dominate, inspect how information enters the context.** Serena targets code access; RTK targets command output. I would measure those sources before deciding to compress the entire history.[^serena][^rtk]

**For facts that must survive across sessions, examine writing, updating, and correction.** Mem0, Graphiti, Hindsight, and MemOS organize memory differently. Ask how an old fact expires, whether its source remains inspectable, whether storage or retrieval adds model calls, and how incorrect records can be removed.[^mem0][^graphiti][^hindsight][^memos]

**For continuity with an assistant you already use, compare integration and handoff behavior.** Headroom, claude-mem, Hindsight, MemOS, and TOMC are worth examining, but their supported clients and automation boundaries differ. A project listing a client does not establish that every request is automatically processed.[^headroom][^claudemem][^hindsight][^memos][^tomc-main]

These are selection suggestions. Without a common evaluation, there is no defensible universal winner in this article.

## 4. What to carry from Claude Code to Codex, or another assistant

Start with a process you can test manually: prepare a working record, give the new assistant that record and the necessary files, then check whether it understands the current state.

This does not require a particular memory product. It also does not transfer accounts, quotas, permissions, or a complete native conversation. The receiving assistant can use only the material its host and configuration allow it to access.

A small `HANDOFF.md` is a useful starting point:

```markdown
# Project handoff

## Current goal
What needs to happen next? What would count as completion?

## Constraints to preserve
Interfaces, dependencies, data scope, and areas that must not be changed.

## Latest valid decisions
Record a source or date for each decision.
Explicitly identify earlier plans that have been withdrawn.

## Current progress
Separate completed work, unfinished work, and work not yet verified.

## Key files and evidence
File paths, relevant commits, test results, and necessary source excerpts.

## Next action
What should happen first? How should it be checked?
What conditions require stopping for clarification?
```

This is a suggested format, not a product-specific requirement.

Before the new assistant starts editing, ask it to restate the active constraints, withdrawn plans, and next verification task. An accurate restatement is an initial check; code, tests, and original materials still need to confirm the work.

Check the packet for credentials, personal information, and restricted data before moving it. Include only material you are authorized to share with the receiving service. A smaller packet can still contain sensitive information.

## 5. A lightweight handoff layer: what is worth testing?

For TOMC, the use case I am targeting is fairly specific: someone already has a preferred model and assistant, carries long working materials, revises decisions over time, and needs both context preparation before the next request and a way to continue elsewhere.[^tomc-main][^tomc-method]

Its core preparation path takes a history, the current task, and a budget. It runs on CPU without training or auxiliary neural model inference. An application using the API must actually call that preparation step and send the resulting context in its subsequent request.[^tomc-method]

One detail worth testing separately is the execution of supported, explicit state operations. For example:

```text
framework = Flask
backup_framework copies framework
framework = FastAPI
```

Under these operations, the current framework is `FastAPI`, while the backup remains `Flask`, the value at the moment of copying. The public implementation supports this normalized syntax and can retain supporting source links. It does not fully interpret arbitrary natural-language negation, implication, or ambiguous references; ordinary prose can instead follow a source-retrieval path.[^tomc-method]

For handoffs, TOMC supports explicitly saving and recalling project notes. Clients on the same computer need to use the same SQLite database to share those notes. Moving between computers requires export/import or a user-managed file workflow. Keep the original history: a context packet prepared for one task can omit evidence needed for a later task.[^tomc-main][^tomc-desktop][^tomc-method]

Automation has a boundary. MCP tools must actually be called. The documented Windows desktop beta also offers an optional local gateway for eligible Codex and Claude Code requests; the documented macOS version does not provide that gateway. WorkBuddy's published setup remains a manual local MCP integration preview, with client tool calls not yet validated. Installation alone does not prove that subsequent requests are smaller.[^tomc-desktop][^tomc-main]

The positioning I would defend today is **a lightweight task-handoff layer for existing assistants**. The core path's lack of auxiliary neural inference, explicit supported state operations, and inspectable handoff materials are a combination of design choices. Whether they produce a consistent advantage over nearby tools needs matched-task testing. I would not claim that this combination is unique across the ecosystem.

## 6. Before trusting a token-saving number, ask three questions

**What is the denominator?** The original history, complete request input, input plus output, and cumulative usage across an entire task are different quantities.

**Was task quality checked?** After removing material, can the assistant still recover the latest constraint, the cause of a failure, or the evidence needed for its next action? Count omissions and human rework.

**What is the full overhead?** Keep the model and accounting method fixed. Record preparation time, extra model calls, and cache conditions. Report token use, elapsed time, and actual cost separately.

Two public TOMC records illustrate why the conditions matter:

| Public record | Reported observation | Limits on interpretation |
|---|---|---|
| **Windows Codex synthetic project-state test** | The same model and host setup were used for nine histories, with five state checks per history. At a 40% history budget, the mean paired reduction in complete request input was **29.7%**. Both this condition and full history scored **45/45** on the checked values.[^codex-test] | Synthetic latest-state questions do not establish lossless general coding performance. These runs selected source blocks rather than producing state-operation records, so they do not isolate the contribution of operation compilation. |
| **User-reported research and slide workflow** | Across 24 matched request pairs, input-plus-output tokens fell from **954,543 to 793,783**, a reduction of **160,760**, or about **16.84%**. Cumulative request time plus preparation fell by **1.12%**.[^cases] | Complete original request receipts are not public. This is not an independent external reproduction or a guarantee of the same benefit for another user. |

In the first record, **40%** describes a history budget; **29.7%** describes a mean of paired reductions in complete request input. The denominators differ. The 45 checked values come from nine related histories and three seeds, not 45 independent projects.[^codex-test]

In the second, token reduction and time reduction differ substantially. The timing covers accumulated requests and preparation, not total human production time.[^cases]

These observations support claims about those particular conditions. They do not establish superiority over all the tools above, a general quality guarantee, or a corresponding reduction in the bill.

## Start with the bottleneck, then compare the whole task

For large inputs, locate the redundant material. For frequently changing facts, test updates and correction. For frequent assistant switching, make the handoff explicit and verify what the receiving assistant understood.

My recommendation is to start with one concrete task. Compare native capabilities, a manually maintained handoff, and the candidate tool. Record missing constraints, repeated explanation, human rework, and end-to-end overhead. Expand only after that comparison gives you useful evidence.

**Carry less history. Keep the work moving.**

---

## Sources

[^lingua]: [Microsoft LLMLingua — official repository](https://github.com/microsoft/LLMLingua).
[^rtk]: [RTK — official repository](https://github.com/rtk-ai/rtk). Check the edition and licensing boundaries.
[^serena]: [Serena — official repository](https://github.com/oraios/serena).
[^toon]: [TOON — official repository](https://github.com/toon-format/toon).
[^headroom]: [Headroom — official repository](https://github.com/headroomlabs-ai/headroom).
[^claudemem]: [claude-mem — official repository](https://github.com/thedotmack/claude-mem).
[^mem0]: [Mem0 — official repository](https://github.com/mem0ai/mem0).
[^graphiti]: [Graphiti — official repository](https://github.com/getzep/graphiti).
[^hindsight]: [Hindsight — official repository](https://github.com/vectorize-io/hindsight).
[^memos]: [MemOS — official repository](https://github.com/MemTensor/MemOS).
[^openviking]: [OpenViking — official repository](https://github.com/volcengine/OpenViking).
[^letta]: [Letta Code — official repository](https://github.com/letta-ai/letta-code).
[^tomc-main]: [TOMC README: integration, shared notes, and product scope](https://github.com/ZipengWu365/TOMC/blob/main/README.md).
[^tomc-method]: [TOMC method semantics and public implementation boundaries](https://github.com/ZipengWu365/TOMC/blob/main/docs/method.md).
[^tomc-desktop]: [TOMC desktop companion: platform differences and handoff materials](https://github.com/ZipengWu365/TOMC/blob/main/docs/desktop_companion.md).
[^codex-test]: [Windows Codex synthetic state test, 5 October 2026](https://github.com/ZipengWu365/TOMC/blob/main/docs/codex_retention_20261005.md).
[^cases]: [TOMC user-reported project records and evidence limitations](https://github.com/ZipengWu365/TOMC/blob/main/casestudy/README.md).
[^claude-native]: [Claude Code: how project memory works](https://code.claude.com/docs/en/memory).
[^codex-native]: [Codex: custom instructions with AGENTS.md](https://developers.openai.com/codex/guides/agents-md/).
