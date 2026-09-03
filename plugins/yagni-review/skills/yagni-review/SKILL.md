---
name: yagni-review
description: Use when explicitly invoked to review a PRD, design document, Implementation Brief, implementation plan, or source code for unnecessary scope or complexity before approval or implementation.
---

# YAGNI Review

## Overview

Reduce the reviewed artifact to the least scope and complexity that achieves the current objective. Review requirements marked "confirmed" as critically as implementation details; confirmation records a decision, not evidence that the decision is necessary.

**Core principle:** keep an item only when omitting it now would fail a current outcome, violate a binding constraint, or create a demonstrated material risk. KISS minimizes total system complexity, not merely lines of code.

## Review contract

1. Establish the current objective, observable success criteria, users or consumers, scale, time horizon, and binding constraints. Include only user-supplied or verified facts. Label unavoidable assumptions; an inferred risk is not permission to invent a mechanism.
2. For repository artifacts, read applicable rules and enough callers, tests, and surrounding code to validate whether an element is used or required.
3. Review the complete artifact, including requirements marked `confirmed`, `must`, `approved`, `standard`, or `best practice`. These labels do not prove present necessity.
4. Treat the result as a recommendation. Do not edit the artifact, change requirements, or implement the simplification unless asked. State source conflicts instead of silently choosing an authority.
5. Use the user's language and the artifact's user-facing terminology.

## Necessity test

Apply these questions to each feature, variant, abstraction, dependency, configuration, fallback, retry, cache, state, integration, operational component, and migration step:

1. Which current objective, acceptance criterion, consumer, or binding constraint requires it?
2. What concrete failure occurs now if it is absent?
3. What current evidence shows that failure is credible?
4. Can an existing mechanism or a more direct design provide the same required outcome?
5. Is adding it later demonstrably irreversible or more dangerous, rather than merely inconvenient?

Assign exactly one disposition:

| Disposition | Use when |
|---|---|
| `Keep` | Removal would break a current outcome, consumer, binding rule, or a correctness, security, privacy, or data-integrity safeguard required by verified system behavior. |
| `Simplify` | The outcome is necessary, but a smaller mechanism meets it. |
| `Remove` | It serves only a hypothetical future, unused generality, speculative scale, preference, or duplication. Remove an edge-case safeguard only when current facts show the case cannot occur or is outside supported scope. |
| `Verify` | A specific unavailable current fact could change the decision, including whether a safeguard is necessary. This is not a softer form of `Keep`. |

## Produce the review

Treat safeguards required by verified system behavior as evidence even when the artifact fails to name them. If evidence is insufficient, use `Verify`; do not guess or delete. Preserve the required outcome without inventing mechanisms or details.

Continue after the first issue. Cite a heading, requirement, task, symbol, or file and line when available.

Use this output shape unless the user requests another:

1. **Verdict** — one short statement of the recommended scope.
2. **Current baseline** — objective, success criteria, and binding constraints.
3. **Findings** — actionable `Remove`, `Simplify`, and `Verify` items, highest impact first. For each, give the evidence, complexity cost or risk, and smallest replacement. Omit empty categories.
4. **Minimum version** — a compact replacement for the reviewed requirements, design, plan, or execution path. Do not introduce unrequested capabilities.
5. **Kept because necessary** — only significant items that might otherwise look removable, with their evidence.
6. **Open decisions** — only decisions that could change the result; omit when empty.

Every `Keep` item must cite a baseline fact or verified evidence. Build `Minimum version` only from paraphrased current-baseline items, evidence-backed `Keep` outcomes, and one strictly smaller replacement for each `Simplify` finding, all at the source's level of abstraction. Current-baseline items include binding legal, contractual, safety, compatibility, and repository constraints. Do not derive implementation steps, fields, states, authentication methods, error cases, or tests from a higher-level outcome. A `Verify` item requires an already-established current obligation with a missing parameter, or a missing fact needed to judge existing code safely; do not ask whether a hypothetical obligation or capability exists. Removed future variations create no design questions. A replacement reduces its cited item and introduces no unrelated "best practice."

If no supported reduction exists, say so. Do not manufacture findings. Preserve removed ideas in a backlog, extension point, design note, feature flag, trigger catalog, or open question only when the user explicitly requests it.

## Example

For a five-user, single-organization pilot whose success criterion is submitting and approving requests:

- `Remove` a generic plugin SDK: it has no current consumer or acceptance criterion.
- `Simplify` twenty notification channels to the one channel currently required.
- `Keep` access control when requests contain personal data.
- `Verify` audit retention only if a contract is known to require audit records but its retention period is unavailable; do not invent a duration.

The minimum version is the request and approval flow plus the evidenced access and audit outcomes—not a platform prepared for hypothetical tenants.

If an acceptance criterion says "read the specified CSV and display two columns," repeat that outcome at the same level; do not expand it into parser options, error branches, fields, or test cases unless the reviewed artifact already requires them.

## Rationalizations to reject

| Rationalization | Response |
|---|---|
| "It is a confirmed requirement, so it cannot be challenged." | Propose re-approval with evidence; confirmation does not prove present necessity. |
| "Authority requires it" or "we already built it." | Authority identifies the decision owner; sunk cost does not establish current value. |
| "We will need it later." | Remove it until a current consumer, constraint, or irreversible decision proves otherwise. |
| "It is best practice." | Name the current failure or binding rule it prevents, or remove it. |
| "A backlog item, extension point, or open question costs almost nothing." | It still creates decisions and maintenance; omit it without a confirmed current need. |
| "KISS means deleting all checks, logs, and error paths." | Necessary safety and correctness are part of the simplest valid system. |
| "While simplifying, we should add this useful metric or abstraction." | Do not replace visible excess with unsupported new scope. |

## Common mistakes

- Calling code unused without checking reachable production callers and framework registration.
- Comparing line counts instead of total operational and cognitive complexity.
- Replacing a generic abstraction with another one that still has only one use.

## Red flags

Stop and re-check the review when it adds an untraced capability, preserves a future-only option, turns a removed item into an open question, or equates KISS with the shortest happy-path code.
