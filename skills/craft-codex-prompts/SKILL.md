---
name: craft-codex-prompts
description: Contract design for Codex task prompts. Use to draft a prompt from requirements, review an existing prompt, or optimize one without changing intended behavior; also use when another Skill needs an embedded Codex task prompt.
---

# Craft Codex Prompts

Treat a Codex prompt as an executable **contract**: define the destination, proof, and operating boundaries while leaving routine implementation choices to the agent.

Use `writing-great-skills` instead when the artifact is a Skill's invocation, information hierarchy, or packaging. Use this Skill for a task prompt embedded in or produced by that Skill.

## 1. Scope the contract

Choose one branch:

- **Draft** from requirements and source material.
- **Review** an existing prompt and diagnose defects before editing.
- **Optimize** while preserving intended behavior and true invariants.

Extract:

- **Observables**: files, repositories, messages, schemas, URLs, tool results, runtime state, and supplied values the agent may inspect.
- **Controls**: reads, local edits, tests, external writes, publication, purchases, destructive operations, and user communication the agent may perform.
- **Guarantees**: final outcome, protected boundaries, evidence standard, validation, and deliverables.

Ask only when an unknown changes authorized scope, creates a significant external effect, or makes success unverifiable. Otherwise declare a bounded assumption.

**Complete when:** every supplied requirement maps to an observable, control, guarantee, declared assumption, or material open question.

## 2. Build the contract

Cover every applicable field once:

| Field | Required behavior |
| --- | --- |
| **Outcome** | State one user-visible goal and exhaustive, checkable success criteria. Use final state or validation, not activity, as proof. |
| **Context** | Rank authoritative inputs; preserve supplied values, exclusions, and protected artifacts; identify retrievable and non-authoritative material. |
| **Control** | Define constraint priority, contextual tool routes, prerequisites, allowed actions, and actions requiring confirmation or prior authority. |
| **Proof** | Define which claims need support, sufficient evidence, citation or attribution behavior, inference labels, and scenario-matched validation. |
| **Recovery** | Define conflict handling, meaningful retry limits, smallest useful fallbacks, blockers, abstention, and stop conditions. |
| **Handoff** | Define long-task phase gates when needed, sparse progress signals, output shape, artifacts, validation report, blockers, and next action. |

Prefer condition-action rules for judgment calls. Reserve `must`, `never`, `always`, and `only` for invariants. Phrase the target behavior positively; pair any necessary prohibition with the allowed alternative.

For **Draft**, or when Review/Optimize requires a full structural rewrite, read [references/prompt-template.md](references/prompt-template.md) before writing. Use only sections that change behavior.

**Complete when:** every applicable field has one authoritative rule, all criteria are observable, and no unresolved conflict is hidden.

## 3. Audit predictability

For **Review** and **Optimize**, or before finalizing a Draft, read [references/review-checklist.md](references/review-checklist.md) and apply every applicable check.

Prune sentence by sentence:

- consolidate duplicated meanings into one source of truth;
- remove no-ops, irrelevant examples, stale context, and routine process instructions;
- replace scattered rules with co-located decision rules;
- preserve safety, permission, business, evidence, validation, output, and stop invariants;
- add only the smallest instruction that fixes an observed failure.

When optimizing a working prompt, change one instruction group at a time and rerun representative cases. Count lower tokens, latency, calls, or cost as an improvement only when required behavior still passes.

**Complete when:** every checklist item passes or appears as a located finding, and the revision preserves every guarantee from Step 1.

## 4. Deliver the branch result

- **Draft**: return the ready-to-use prompt, then material assumptions and unresolved inputs.
- **Review**: return findings in descending impact with quoted or located evidence, then the smallest sufficient revision and a short change map.
- **Optimize**: return the compact prompt, meanings removed or consolidated, invariants preserved, and a representative evaluation plan.

Place findings and explanatory material outside the copy-ready prompt artifact.

**Complete when:** the requested branch output is copy-ready, every deliverable is present, validation is reported, and remaining uncertainty or human action is explicit.
