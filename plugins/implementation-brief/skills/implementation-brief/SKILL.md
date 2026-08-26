---
name: implementation-brief
description: Use when the user explicitly requests an implementation brief after grilling, grill-me, a requirements interview, or another decision-making session has concluded.
---

# Implementation Brief

Turn settled decisions from the current conversation or user-supplied notes into an implementation-ready handoff.

## Source of truth

Use only information already confirmed by the user. Classify content as follows:

| Content | Treatment |
|---|---|
| Confirmed decision or fact | State it directly |
| Useful inference or recommendation | Label it `Recommendation` and give the reason |
| Missing or unresolved detail | Put it under `Open questions`; do not guess |

If the current conversation contains no usable decisions, ask the user to paste the grilling result or decision notes and stop.

## Output contract

Respond with one Markdown brief in the user's language, using this order. The labels below define each section's meaning; translate every heading rather than copying the English labels when the user is using another language.

1. `# Implementation Brief: <title>`
2. `## Objective and success`
3. `## Context`
4. `## Confirmed requirements`
5. `## Scope`, with `In scope` and `Out of scope`
6. `## Implementation direction`
7. `## Known affected areas`
8. `## Constraints and edge cases`
9. `## Acceptance criteria`
10. `## Verification`
11. `## Open questions`

Keep requirements traceable to the source decisions. Each fact belongs in the single most relevant section. Unresolved decisions appear only under `Open questions`, not in constraints or other sections. Limit open questions to decisions that must be settled before implementation; repository facts that an implementer can discover are not user questions. Use `None confirmed` or `Not identified` when a required section has no confirmed content. Acceptance criteria must be observable outcomes; verification must name the checks implied by the confirmed requirements.

Output the brief directly in the terminal response. Do not create or update a brief file, modify the repository, start implementation, or silently continue the interview. Do not add a preamble or completion message outside the brief.

## Common mistakes

- Turning a plausible implementation detail into a confirmed requirement
- Hiding unresolved decisions inside recommendations
- Repeating the same requirement across multiple sections
- Treating discoverable repository details as questions for the user
- Writing a plan with task estimates instead of a concise implementation handoff
