# Prompt contract template

Read this file when drafting a prompt or replacing an existing prompt's structure. Include only sections that change agent behavior.

```text
Role
[Agent function and task context. Omit when obvious.]

Outcome
Goal: [one user-visible final state]

Success criteria:
- [observable result]
- [required artifact or external state]
- [validation signal]
- [protected item that remains unchanged]

Context
- Authoritative inputs, in order: [...]
- Inspectable workspace or runtime state: [...]
- In scope: [...]
- Out of scope or protected: [...]
- Preserve these supplied values: [...]
- Retrieve [material] when [decision requires it].

Control
- Constraint priority: [safety/permission, business/data, evidence/validation, scope, presentation]
- If constraints conflict: [condition-action rule]
- Use [tool] when [condition]; rely on [return field or artifact].
- Resolve these prerequisites before acting: [...]
- Independent reads may run in parallel; dependent actions remain sequential.
- Allowed without confirmation: [...]
- Requires confirmation or prior authority: [...]

Proof
- Claims requiring support: [...]
- Sufficient evidence: [...]
- Citation or attribution form: [...]
- Label inference and uncertainty as: [...]
- Required validation: [...]
- If evidence or validation is unavailable: [...]

Recovery
- Retry [failure] at most [N] times when [...], then [fallback].
- Treat empty, partial, stale, or conflicting results as: [...]
- Block when [...].
- Abstain or narrow the result when [...].
- Stop when all success criteria pass, or when [...].

Handoff
- Phases and completion gates, if long-running: [...]
- Update only at major phase changes, plan-changing findings, or blockers.
- Output format, audience, language, and length: [...]
- Deliverables and paths or naming rules: [...]
- Final handoff: completed state, changes, validation, unverified items, blockers, required human action, and relevant Git/global-config state.
```

## Decision rules

- Treat missing evidence as missing, not as proof of absence. Narrow the conclusion or report the gap instead of guessing.
- Make another retrieval call only for a required fact, date, identifier, source, comparison, or requested exhaustive coverage.
- Match validation to the artifact: tests/builds for code, reopen/render checks for documents, smoke checks for apps, and remote read-back for publication.
- Permit in-scope local changes and non-destructive validation for change/build/fix requests. Keep implementation and publication outside answer/review/diagnose/plan authority unless requested.
- Require confirmation or explicit prior authority for destructive actions, external writes, purchases, credential or production changes, sensitive-data exposure, and material scope expansion.
- Block only for missing authority, credentials, a material user choice, unavailable required evidence, or an unsafe required action after safe in-scope work and meaningful fallbacks are exhausted.
- For long tasks, use outcome-based phases such as discover, design, execute, validate, and deliver. Preserve a compact state capsule after major milestones: objective, completed work, evidence, decisions, blockers, and next permitted action.
