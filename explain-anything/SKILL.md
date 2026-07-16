---
name: explain-anything
description: Explain anything the user asks about — a file, function, system, concept, algorithm, config, error, command, or process — by walking its logic in plain English, anchored to the real source with a concrete example. Use when the user wants something explained, asks "how does this work", "walk me through", "what does this do", or "explain <anything>". Accepts an optional depth (quick / normal / deep).
disable-model-invocation: true
argument-hint: "<anything to explain> [quick|normal|deep]"
---

# Explain Anything

Explain whatever the user asks the way a patient senior engineer would at a whiteboard: show the **real thing**, trace the **logic in plain English**, and ground it in a **concrete example**. The reader should walk away able to predict what happens on a given input.

This works for anything — code, but equally a system, concept, algorithm, config, error message, command, or process. You are explaining, not reviewing: don't critique or suggest changes unless asked.

## How to explain

1. **Read the target first.** Never explain from the name or your assumptions. Read the actual file/error/command and one level around it — enough to explain honestly, no more. For a general concept with no local source, explain from real knowledge and flag what's general vs. specific to this codebase. If the target is ambiguous, ask which one before explaining.

2. **Pick the depth** (from the request; default **normal**):
   - **quick** — one paragraph: what it is and the single key idea.
   - **normal** — the full shape below, focused on the main path.
   - **deep** — plus edge cases, error paths, and why it's built/works this way.

3. **Explain in this shape:**
   - **What it is** — one sentence a non-expert could follow.
   - **How it works** — the core. Walk the logic step by step in plain English ("first it checks X, if empty it falls back to Y…"), pairing each step with the **real source** it's about (snippet, command, or config line, with `file_path:line` when from a file). Narrate the logic, not a line-by-line transcript.
   - **A concrete example** — trace a realistic input to a specific output.
   - **A sketch** — an ASCII diagram or ordered list, only when structure (branches, pipelines, call chains) makes it clearer.

4. **Close by checking in.** Name the parts you didn't expand and offer to go deeper, rather than dumping everything at once.

## Constraints

- Plain English for the logic; real source for the anchor. No invented or paraphrased source.
- If a branch, error path, or caveat matters, include it. If you didn't read something, say so instead of guessing.
- Match the depth requested.
