---
name: make-knowledge-cards
description: Turn a pasted article or local Markdown or TXT file into a small set of source-grounded knowledge cards. Use when a user wants key ideas extracted, deduplicated, and explained; do not use for web retrieval, PDFs, Anki decks, or graphical card design.
---

# Make Knowledge Cards

Convert the full supplied article into concise, useful knowledge cards. The normal target is 5–8 cards, but source fidelity takes priority over reaching a count: return fewer when the article contains fewer distinct, useful ideas, and say briefly why. Never split one idea just to increase the count.

## Input

- Accept text pasted by the user, or a local `.md` or `.txt` file the user identifies or attaches.
- Read the supplied file as a whole before selecting ideas. If it cannot be read, is empty, or only part of it is available, state that limitation and do not imply that the entire article was reviewed.
- If the input is a URL, PDF, or another unsupported format, explain the boundary and ask for pasted text or a Markdown/TXT copy. Do not fetch or convert it.

## Make the cards

1. Identify the article's main claim and the distinct ideas needed to understand or apply it. Prefer central concepts, causal links, decision rules, methods, and qualifications over anecdotes, repeated restatements, and minor details.
2. Merge repeated ideas. Keep each card focused on one independently useful knowledge point; do not make neighboring cards paraphrase one another.
3. Stay within the source. Do not add outside facts, assumed context, invented statistics, causes, or examples. Preserve caveats, uncertainty, scope, and attribution. When the article asserts a conclusion without showing support, present it as the author's claim rather than supplying a rationale. If the source is ambiguous or internally inconsistent, keep that uncertainty visible instead of silently resolving it.
4. Give each card a concise title, the core knowledge, and a plain explanation. Add an example only if the article supplies or directly supports one. Otherwise use a self-test question answerable from the article; do not invent an answer or scenario requiring outside knowledge.
5. Choose the final number by distinct source-supported ideas. Aim for 5–8 where the article supports that many. If it does not, provide the smaller useful set and briefly note that the source did not support more without repetition or inference.

## Output

Respond in Markdown, normally in the source language. Use this structure for every card:

### 卡片 1｜标题
- **核心知识：** one sentence stating the point.
- **简明解释：** explain what it means or how it works, using only source-supported information.
- **例子：** an example from the source; or
- **自测：** a question answerable from the source, with a short answer.

Use either `例子` or `自测` per card, not both by default. If a source gives no usable example, prefer a self-test. After the cards, add a brief note only when fewer than five cards were supported, input coverage was limited, or a source ambiguity materially affects interpretation. Do not add citations or source locations unless useful for distinguishing claims or requested by the user.

## Boundaries

This skill does not retrieve webpages, process PDFs, create Anki decks, or design/render graphic cards. It returns text-based knowledge cards only.
