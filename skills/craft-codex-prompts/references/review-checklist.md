# Prompt contract review

Read this file when reviewing or optimizing a prompt, and before finalizing a newly drafted prompt. Inspect the prompt before rewriting it.

## Findings

Report defects in descending impact:

- **Critical**: contradiction with higher instructions, unsafe or ambiguous authority, unverifiable completion, missing required evidence, or a stop rule that permits a false success.
- **Material**: unclear scope, weak tool routing, absent fallback, hidden conflict, incomplete handoff, or a long-task phase without a gate.
- **Compression**: duplicated meaning, no-op, irrelevant example, stale context, scattered rule, unnecessary absolute, or avoidable negative steering.

Locate each finding with a quote, heading, or line. Explain the behavior it can change; omit purely stylistic preferences.

## Contract checks

- **Outcome**: one clear goal; success criteria are observable and exhaustive; activity is not treated as proof.
- **Context**: authoritative inputs are ranked; supplied values, exclusions, and protected artifacts survive; large or conditional material has a reliable context pointer.
- **Control**: priorities resolve ordinary conflicts; tool routes state conditions and prerequisites; local actions, external effects, approvals, and scope expansion are separated.
- **Proof**: support and citation rules identify sufficient evidence; fact, inference, uncertainty, source conflict, and absence are handled; validation matches the user scenario.
- **Recovery**: retries are meaningful and bounded; fallbacks are smaller and useful; blockers require a real external change; stop rules prevent both premature completion and endless polishing.
- **Handoff**: long work has phase gates and sparse updates; output, artifacts, validation, unverified items, blockers, and next actions are testable.

## Pruning checks

For each sentence, ask:

1. Does it change behavior versus the model's default?
2. Is this meaning already stated elsewhere?
3. Is it needed by this branch, or should it sit behind a context pointer?
4. Does it state the target behavior, or merely name a prohibited behavior?
5. Is an absolute word guarding an invariant, or replacing a decision rule?

Delete a failed no-op sentence instead of decorating it. Consolidate duplication at the more authoritative location. Preserve one compact leading term when it replaces repeated explanation without losing the decision rule.

## Revision and validation

Make the smallest revision that resolves all Critical and Material findings. Preserve the original outcome and guarantees unless the user changes them.

For optimization, remove or revise one instruction group at a time, then rerun the same representative cases. Compare:

- correctness and completeness;
- evidence and required citations;
- tool choice, calls, turns, retries, and approvals;
- blockers and stop behavior;
- tokens, latency, and cost after quality passes.

The review is complete when every contract and pruning check passes or is reported as an unresolved finding, and every preserved guarantee remains represented once in the revised prompt.
