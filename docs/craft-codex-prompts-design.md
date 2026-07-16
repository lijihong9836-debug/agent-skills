# `craft-codex-prompts` design notes

## Purpose

`craft-codex-prompts` guides an agent that is writing, reviewing, or optimizing instructions for Codex. Its output is an agent-facing task contract: goal, success criteria, context, authority, evidence, tools, failure behavior, stop rules, and deliverables.

It is not a general prompt-writing guide for ordinary users and does not own Skill packaging or invocation design.

## Source synthesis

The design draws on two inputs:

- OpenAI's [Prompting guidance for GPT-5.6](https://developers.openai.com/api/docs/guides/prompt-guidance-gpt-5p6), especially outcome-first contracts, completion and stop conditions, lean prompts, autonomy boundaries, contextual tool routing, grounding, long-running state, and validation.
- The existing `writing-great-skills` reference, especially predictability, checkable completion criteria, information hierarchy, progressive disclosure, single-source-of-truth pruning, duplication and no-op detection, positive steering, and premature-completion diagnosis.

The Skill converts those ideas into operational drafting rules, a reusable prompt template, and a review checklist. It intentionally does not reproduce the official guide's prose, benchmark narrative, API migration advice, or model-specific feature catalog.

## What is reused from `writing-great-skills`

| Reused concept | Application here |
| --- | --- |
| Predictability | Treat the prompt as an executable contract whose process and completion bar are stable. |
| Completion criteria | Require observable success criteria and phase gates instead of activity lists. |
| Information hierarchy | Keep core task rules in the prompt and put conditional or large material behind context pointers. |
| Progressive disclosure | Retrieve large or branch-specific context only when the decision requires it. |
| Single source of truth | State each constraint once and consolidate overlapping approval, evidence, or style rules. |
| Duplication and no-op tests | Remove repeated meanings, generic exhortations, irrelevant examples, and routine process instructions. |
| Positive steering | State the desired action and reserve prohibitions for hard guardrails. |
| Premature completion | Add checkable phase gates, validation, and stop conditions. |

## What is adjusted

| `writing-great-skills` concern | Adjustment for agent prompts |
| --- | --- |
| Skill invocation and descriptions | Out of scope here; prompts are already in the active task context. |
| Skill steps versus reference | Reframed as task contract versus retrievable context and source authority. |
| Split by invocation or sequence | Reframed as long-thread phases with authority gates and state capsules. |
| Leading words | Optional compression aid, not a required prompt mechanism; explicit decision rules take precedence. |
| Completion criteria | Expanded to cover evidence sufficiency, validation, approval boundaries, blockers, and handoff state. |
| Context load | Expanded to include irrelevant tools, repeated examples, stale thread state, and unnecessary process narration. |

## New responsibilities

The new Skill adds concerns that are central to Codex task prompts but not the responsibility of a Skill-writing reference:

- observable inputs, controllable actions, and required guarantees;
- source authority and explicit evidence sufficiency;
- permission tiers and external-effect boundaries;
- contextual tool routing, prerequisite retrieval, and bounded fallback behavior;
- conflict priority and preservation of explicit user values;
- retry, abstention, blocking, and stop conditions;
- long-running phase gates, sparse progress updates, and compact state transfer;
- output schemas, artifact paths, validation results, and final handoff requirements;
- prompt review by severity and behavior-preserving optimization through representative evaluation.

## Responsibility boundary

Use `writing-great-skills` when the artifact being designed is a Skill: its invocation behavior, frontmatter description, information hierarchy, progressive disclosure, granularity, and maintenance discipline.

Use `craft-codex-prompts` when the artifact being designed is an instruction set for Codex to execute a task: its outcome, scope, authority, evidence, tools, failures, stopping behavior, and delivery contract.

When a Skill contains a reusable task-prompt template, apply both without duplicating ownership:

1. Let `writing-great-skills` govern the Skill package and where the template lives.
2. Let `craft-codex-prompts` govern the embedded template's task contract.
3. Keep shared concepts, such as completion criteria or pruning, in the owning layer and reference them rather than restating them across files.

## Design decisions

- The Skill is model-invoked because agents should discover it during prompt drafting and review work.
- The body stays in one file because all three branches need the same contract model and checklist; splitting would add navigation without reducing branch load.
- The distributable Skill contains only `SKILL.md` and UI metadata. Repository rationale remains under `docs/` so installation does not load maintenance history.
- Absolute language is limited to invariants; contextual decisions use explicit condition-action rules.
- Optimization is behavior-preserving and evaluation-driven. Lower token use is not considered an improvement when correctness, evidence, or required delivery regresses.
