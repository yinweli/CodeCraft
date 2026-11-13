---
name: code-craft
description: >
  Implement, modify, and verify application code with minimal, focused changes.
  Use for feature development, bug fixes, code changes, refactoring requested by
  the user, and related test/build/lint verification. Apply project conventions
  and language-specific coding rules when relevant.
---

# CodeCraft

Implement only the requested change, following the project's existing design and conventions.

## Principles

- KISS and YAGNI: fewest components and states that work; no abstractions for speculative needs. Explain any necessary complexity.
- Do not extrapolate second- or third-order requirements from hypothetical scenarios. Leave questions that do not affect the current decision or implementation unexplored.
- Cover the main flow and common cases; handle edge cases only when reasonably likely or high-impact.
- Reuse existing structures, APIs, libraries, and terminology. Prefer localized changes; do not refactor unrelated code.
- Do not expand public APIs merely to make testing easier.
- Do not edit generated code; change its source or generator.

## Applying Conventions

- The conventions below apply to lines you write or modify. Do not convert untouched lines, even in the same function, and do not create formatting-only diffs — unless the user explicitly asks to apply the conventions to existing code.
- More specific project rules (instructions, linter/formatter config) take precedence. If a project linter rejects a convention below, follow the linter and mention the conflict in the report.

## General Conventions

- Use Traditional Chinese for responses, code comments, and work records unless the project or user specifies otherwise.
- Use English identifiers; keep established technical names and project terminology.
- Name variables, parameters, fields, and named return values in the singular, **including collections**:
  `user := []User{}`, `List<Order> order`, `func load() (item []Item, err error)`.
- Use `itor` for a loop element when there is no more specific domain name; use `k, v` for map key/value:
  `for _, itor := range user { ... }`, `for k, v := range score { ... }`, `foreach (var itor in order) { ... }`.
- Comments explain reasons, constraints, and non-obvious intent, not what each line does.

## Go and C# Conventions

- Test true directly and false explicitly — never `== true`, never `!`:
  `if ready { ... }` / `if (ready) { ... }`; `if ready == false { ... }` / `if (ready == false) { ... }`.
- Always add a closing comment naming the keyword at the end of every control-flow block (`if`, `for`, `foreach`, `while`, `switch`, `select`, `try`, etc.), regardless of length: `} // if`, `} // for`, `} // switch`.
  For an `if`/`else` chain, add it only after the final branch. Never add one at the end of a function, method, type, or closure.

## Go Conventions

- Always use a parenthesized `import` block, even for one package.
- Multiple return values: name every one, e.g. `func parse(s string) (result Config, err error)`. Single return value: unnamed, e.g. `func count() int`.
- Filenames: lowercase for one word (`server.go`), lowerCamelCase for compound names (`commandMove.go`, `commandMove_test.go`).
- Order type-related declarations as: type definition → constructor → methods.

## Workflow

1. **Inspect:** Read relevant requirements, code, tests, and project instructions. Check the working tree first; preserve unrelated existing changes.
2. **Implement:** Make the smallest sound change; touch only relevant files.
3. **Verify:** Run the existing tests, linters, and builds relevant to the change. Never invent commands or claim unrun checks passed.
4. **Report:** Summarize the change, checks run and their results, failures, limitations, and open issues.

## Verification and Safety

- When verification fails, separate failures caused by this change from pre-existing ones; do not fix unrelated problems to get a green result.
- If a test contradicts a confirmed authoritative specification, use the specification to decide whether the test or the code is wrong. Do not silently change requirements.
- Keep temporary scripts and artifacts in the project's designated temp directory, or a task-specific temp location if none exists; clean up only what this task created. Do not assume a directory is Git-ignored.
- Do not commit, push, rebase, reset, or merge unless explicitly authorized.
- If the user requests analysis only, do not modify files.
