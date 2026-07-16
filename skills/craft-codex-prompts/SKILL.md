---
name: craft-codex-prompts
description: Draft, review, and optimize prompts that instruct Codex or another coding agent. Use when an agent needs to turn a task brief, operating policy, tool workflow, long-running assignment, or existing prompt into a precise agent-facing contract with goals, success criteria, evidence rules, tool and permission boundaries, failure handling, stop rules, and deliverable requirements. Do not use for ordinary end-user copywriting or for designing the structure and invocation metadata of a Skill itself.
---

# Craft Codex Prompts

Treat an agent prompt as an executable contract. Define the destination, the proof of completion, and the operating boundaries; leave implementation choices open unless a sequence is safety-critical, externally imposed, or proven fragile.

## Choose the branch

- **Draft**: turn requirements and source material into a new Codex prompt.
- **Review**: identify defects in an existing prompt before proposing edits.
- **Optimize**: preserve intended behavior while removing contradictions, duplication, no-ops, irrelevant tools, and over-prescribed process.

If the request is to create or revise a Skill, use the Skill-authoring workflow for its structure, metadata, progressive disclosure, and packaging. Apply this Skill only to agent prompts embedded in or produced by that Skill.

## Build the prompt contract

### 1. Establish the task model

Extract three sets before drafting:

1. **Observable inputs**: files, repositories, messages, schemas, source URLs, tool results, runtime state, and user-supplied values the agent may inspect.
2. **Controllable actions**: reads, local edits, tests, external writes, publication, purchases, destructive operations, and user communication the agent may perform.
3. **Required guarantees**: user-visible outcome, preserved boundaries, evidence standard, validation, and final delivery state.

Record material unknowns. Ask only when an unknown would change the authorized scope, create a significant external effect, or make success unverifiable. Otherwise state a bounded assumption and proceed.

### 2. Define goal and completion

Write one outcome-first goal. Describe the final state, not a transcript of steps.

Add checkable success criteria. Each criterion must identify an observable result, artifact, state, or validation signal. Include every required deliverable and any protected item that must remain unchanged.

Use completion language such as:

```text
Success means:
- [observable result]
- [required artifact or state]
- [validation that must pass]
- [protected boundary that must remain intact]
```

Do not use activity as proof of completion. “Inspect the repository” or “run tests” is a step; the completion criterion is the finding produced or the named checks passing.

### 3. Bound context and sources

Name the authoritative inputs and their order of authority. Distinguish:

- task-specific source material;
- current workspace or runtime state;
- durable project instructions;
- external sources that require retrieval;
- background information that is informative but non-authoritative.

State what is out of scope. Preserve explicit user values and named exclusions. Do not replace supplied values with guessed defaults, keyword maps, or broad semantic shortcuts.

When a prompt references large material, give a context pointer that says when to read it and what decision it supports. Do not paste material the agent can retrieve reliably.

### 4. Define tools and action boundaries

Expose or name only task-relevant tools. For each non-obvious tool route, state:

- what the tool resolves;
- when it is required or preferred;
- prerequisites and permission level;
- the return fields or artifact that matter;
- what empty, partial, stale, or failed results mean.

Parallelize independent reads. Keep dependent actions sequential. Synthesize parallel results before mutating state.

Require prerequisite discovery, retrieval, and validation when correctness depends on them. Do not allow the agent to skip a prerequisite because the likely final answer appears obvious.

Use a bounded programmatic or batch stage only when deterministic filtering, joining, sorting, deduplication, aggregation, or repeated validation materially reduces intermediate data. Name eligible tools, output schema, retry limit, stop condition, and handoff back to model judgment.

### 5. Set autonomy and approval boundaries

Match authority to the request type:

- For answer, explain, review, diagnose, or plan requests, allow relevant inspection and reporting. Do not imply authority to implement or publish.
- For change, build, fix, or convert requests, allow in-scope local changes and non-destructive validation.
- Require confirmation or explicit prior authorization for destructive actions, external writes, purchases, credential changes, production changes, sensitive-data exposure, or material scope expansion.

State this policy once. Do not scatter “ask first” rules across the prompt. Prefer a decision rule over a blanket approval requirement.

### 6. Order constraints and resolve conflicts

Group constraints by function: safety and permissions, business or data boundaries, evidence and validation, scope, then presentation. State each meaning once.

When requirements conflict:

1. Preserve higher-level instructions and true invariants.
2. Preserve explicit user values and protected boundaries within the allowed scope.
3. Prefer correctness, required evidence, and safety over speed, brevity, or fewer tool calls.
4. Prefer required content over optional style.
5. Surface unresolved conflicts that materially change the result; do not silently choose.

Do not claim that a task prompt overrides system, developer, policy, permission, or applicable workspace instructions.

Reserve **must**, **never**, **always**, and **only** for true invariants. For judgment calls, write the condition and action: “If X, do Y; otherwise Z.” Phrase the target behavior positively; keep prohibitions for hard guardrails and pair them with the allowed alternative.

### 7. Specify evidence and verification

Define which claims require support and what counts as sufficient evidence.

For grounded work:

- cite or identify only sources actually retrieved;
- attach support to the claim it establishes;
- separate verified fact, inference, and uncertainty;
- state material source conflicts;
- treat missing evidence as missing, not as proof of absence;
- narrow the conclusion or report the gap instead of guessing.

For artifact work, require validation that matches the user scenario: targeted tests and builds for code, reopen or render checks for documents, smoke checks for apps, and remote read-back for publication. If a check cannot run, require the agent to name the unverified item, reason, and next best check.

Set a retrieval budget with decision rules. Permit another lookup only when a required fact, date, identifier, source, comparison, or exhaustive coverage remains missing. Do not retrieve again only to improve prose or add optional detail.

### 8. Define failure, fallback, and blocking

For each material dependency, specify the smallest useful fallback. A robust rule names:

- retryable versus terminal failures;
- maximum meaningful retries;
- fallback source, tool, or reduced-scope path;
- the evidence needed before declaring no result;
- the condition that requires user input or new authority.

Block when success requires missing authority, credentials, a material user choice, unavailable required evidence, or an unsafe action. Do not label difficulty, slow progress, or an optional clarification as a blocker while safe in-scope work remains.

### 9. Control long-running work

Divide long tasks into outcome-based phases such as **discover**, **design**, **execute**, **validate**, and **deliver**. Define a completion gate for each phase and prevent silent movement into a layer that needs new authority.

Require a short preamble before the first tool call and sparse updates only when a major phase begins, a finding changes the plan, or a blocker appears. Each update states one concrete outcome and the next step. Do not request narration of routine calls.

Maintain a compact state capsule after major milestones:

```text
Objective:
Completed:
Evidence:
Decisions and assumptions:
Blockers:
Next permitted action:
```

Stop when all success criteria pass, a defined blocker requires external change, meaningful fallbacks are exhausted, no safe in-scope action remains, or the user replaces the objective. Do not continue searching or polishing after the completion bar is met.

### 10. Specify output and handoff

Name the required output shape, artifact paths or naming pattern, language, audience, and length only when they affect usefulness. Prioritize required facts, decisions, caveats, evidence, blockers, and next actions; trim introductions, repetition, generic reassurance, and optional background first.

Require the final handoff to distinguish:

- completed work and resulting state;
- files or external objects changed;
- validation performed and results;
- remaining unverified items;
- blockers and exact human action required;
- whether Git or global configuration was touched, when relevant.

## Prompt template

Use only the sections that change behavior.

```text
Role
[Agent function and task context. Omit if obvious.]

Goal
[One user-visible outcome.]

Inputs and scope
- Authoritative inputs: [...]
- Inspectable context: [...]
- In scope: [...]
- Out of scope / protected: [...]

Success criteria
- [Observable result]
- [Artifact or state]
- [Required validation]

Constraints and priority
- [Safety, permission, business, data, or compatibility constraints]
- If constraints conflict: [decision rule]

Evidence and verification
- Claims requiring support: [...]
- Sufficient evidence: [...]
- Required checks: [...]
- If evidence or checks are unavailable: [...]

Tools and autonomy
- Use [tool] when [condition]; rely on [return field/artifact].
- Independent reads may run in parallel; dependent actions remain sequential.
- Allowed without confirmation: [...]
- Requires confirmation or prior authority: [...]

Failure and stop rules
- Retry [failure] at most [N] times, then [fallback].
- Block when [...].
- Stop when all success criteria pass or [...].

Workflow state
- Phases and gates: [...]
- Update only at major phase changes or blockers.

Output and delivery
- Format: [...]
- Deliverables: [...]
- Final handoff must include: [...]
```

## Review and optimization

Review an existing prompt before rewriting it. Report defects in descending impact, then provide the smallest revision that fixes them.

Use this checklist:

- **Outcome**: Is there one clear goal and a checkable completion bar?
- **Scope**: Are authoritative inputs, exclusions, preserved values, and protected artifacts explicit?
- **Authority**: Are local actions, external effects, approvals, and scope expansion separated?
- **Priority**: Are constraints grouped, non-duplicated, and conflict-resolvable?
- **Evidence**: Are support, citation, inference, absence, and validation rules operational?
- **Tools**: Are routes contextual, prerequisites explicit, and error behavior bounded?
- **Failure**: Are retry, fallback, blocking, and abstention conditions defined?
- **State**: For long work, do phases have gates, sparse updates, and stop rules?
- **Delivery**: Are output shape, artifacts, verification, and handoff requirements testable?
- **Economy**: Does every instruction change behavior? Remove repeated meanings, generic exhortations, irrelevant examples, and process the agent already performs reliably.
- **Language**: Replace unnecessary absolutes with decision rules and negative steering with the desired action.

Treat contradictions, unverifiable success criteria, unsafe authority, and missing required evidence rules as critical defects. Treat duplicated style guidance, routine-process narration, and non-behavioral examples as compression opportunities.

For optimization, preserve the original task outcome and true invariants. Remove one instruction group at a time and validate on representative tasks. Add only the smallest targeted instruction that fixes an observed failure. Compare correctness and completeness before counting lower tokens, latency, calls, or cost as an improvement.

## Branch outputs

- **Draft**: return the ready-to-use prompt, followed by material assumptions and unresolved inputs.
- **Review**: return findings by severity with quoted or located evidence, then a revised prompt and a short change map.
- **Optimize**: return the compact prompt, meanings removed or consolidated, invariants preserved, and a representative evaluation plan.
