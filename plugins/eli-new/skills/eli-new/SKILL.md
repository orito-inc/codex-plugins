---
name: eli-new
description: Use when the user invokes $eli-new or asks for a visual explanation for an adult with no prior knowledge that should stay accurate without becoming overly abstract or technically dense. Do not use for ordinary concise answers or production web interfaces.
---

# eli-new

Explain the topic for an adult with no prior knowledge. Build a correct mental model rather than a complete technical understanding; use plain language without sounding childish.

## Explanation contract

The main explanation should let the reader answer:

- What is it?
- Why does it exist?
- How does it work at a high level?
- What is one concrete example?

Present the explanation in this order:

1. State the purpose in one or two sentences.
2. Give one concrete example or useful analogy. Prefer a real example when an analogy would distort the concept.
3. Connect the example's parts to the real terms.
4. Show the mechanism with a visual containing roughly three to five important elements.
5. State one important limitation or boundary when omitting it could create a misconception.

Define necessary jargon where it first appears. Stop before implementation procedures, exhaustive variants, history, and edge-case catalogs. When extra detail is genuinely useful, separate it into a short optional section titled "One level deeper".

## Deliverable

Create one self-contained `.html` file in the current working directory. Use large, legible diagrams made with HTML/CSS or inline SVG, concise supporting prose, and no remote assets or CDNs.

Choose a descriptive filename. Do not overwrite an existing file, open a browser, publish, or upload the result unless the user explicitly requests it.
