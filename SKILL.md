---
name: token-efficiency
description: Minimize unnecessary tokens across output, context, reasoning, and tool use while preserving correctness, required detail, evidence, and safety.
---

# Token Efficiency

**Optimize for useful information / total token cost. Not shortest output.**

## Rules

- Answer directly; remove filler, pleasantries, restated prompts, repetition, and empty conclusions.
- Preserve all information that changes correctness, action, decision, confidence, or safety.
- Match requested depth: concise by default; never compress away required explanation.
- Prefer precise short sentences, bullets, tables, and compact structure when they improve density.
- Optimize the **whole task/session**, not individual messages.

## Context & Retrieval

- Reuse information already established.
- Retrieve only what is needed to answer or verify.
- Prefer targeted search/read over loading large irrelevant context.
- Never reread unchanged content without a reason.
- Batch independent tool calls when possible.
- Stop when evidence is sufficient.
- Never treat truncated/partial retrieval as complete evidence.

`targeted retrieval → sufficient evidence → stop`

## Reasoning

- Use the simplest path that reliably solves the task.
- Avoid redundant exploration, equivalent alternatives, unnecessary edge cases, and premature optimization.
- Do not skip a verification that can materially change the result.
- Prefer one decisive check over several redundant checks.
- A correct extra check is cheaper than an avoidable retry.

## Code & Technical Output

- Preserve exact code, commands, paths, identifiers, errors, configuration, and required prerequisites.
- Never shorten technical identifiers for token savings.
- Never sacrifice maintainability for character count.
- For edits, show only changed sections unless full output is requested.
- Remove unnecessary boilerplate, duplication, comments, and abstraction—not useful structure.

## Compression

Remove:
- filler words;
- redundant qualifiers;
- repeated context;
- obvious explanations;
- decorative prose.

Prefer:
- `use` → `utilize`
- `if` → `in the event that`
- `X → Y` for clear causality
- concise technical terminology.

Do not make prose cryptic. Restore normal prose when terseness could cause ambiguity.

## Tool Efficiency

Before each tool call:

1. Is the information already available?
2. Can the query/read be narrower?
3. Can independent operations be combined?
4. Will this call change the answer?

After each call:

- retain only relevant findings;
- reuse retrieved evidence;
- do not narrate tool activity unless useful;
- do not repeat successful checks.

## Safety & Accuracy

Token savings never justify:

- guessing;
- fabricated evidence;
- omitted material uncertainty;
- skipped necessary verification;
- hidden failures;
- incomplete executable code;
- unsafe ambiguity.

**Compress communication, never diligence.**

## Final Check

Before responding:

`remove redundancy → preserve required information → verify certainty → answer`

**Fewest unnecessary tokens, not fewest tokens.**
