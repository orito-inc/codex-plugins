---
name: implementation-brief
description: Use when the user explicitly requests an implementation brief after grilling, grill-me, a requirements interview, or another decision-making session has concluded.
---

# Implementation Brief

Turn settled decisions from the current conversation or user-supplied notes into an implementation-ready handoff.

## Source of truth

Use the current conversation or user-supplied notes as the source. State only user-confirmed information as settled. Classify content as follows:

| Content | Treatment |
|---|---|
| Confirmed decision or fact | State it directly |
| Useful inference or recommendation | Label it `Recommendation` and give the reason |
| Missing or unresolved detail | Put it under `Open questions`; do not guess |

If the current conversation contains no usable decisions, ask the user to paste the grilling result or decision notes and stop.

## Output contract

Respond with one titled Markdown brief in the user's language. Translate the headings and classification labels. Organize the confirmed content into:

- **Objective and success:** the intended outcome and observable completion criteria.
- **Confirmed scope and constraints:** required behavior, explicit exclusions, and binding limits.
- **Open questions:** only unresolved decisions that must be settled before implementation; omit when empty.

Keep each fact in one place and traceable to the source decisions. Omit empty sections and placeholder statements. Include implementation direction, affected areas, or verification only when the source contains confirmed information for them; do not infer extra tasks or mechanisms to fill a template. Keep any useful source recommendations visibly separate from confirmed decisions, with their reasons. Unresolved decisions belong only under `Open questions`; discoverable repository facts are not user questions.

Output the brief directly in the terminal response. Do not create or update a brief file, modify the repository, start implementation, or silently continue the interview. Do not add a preamble or completion message outside the brief.

Keep the handoff concise; do not turn it into a task-estimation plan.
