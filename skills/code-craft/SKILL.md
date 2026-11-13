---
name: code-craft
description: >
  Implement, modify, and verify application code with minimal, focused changes.
  Use for feature development, bug fixes, code changes, refactoring requested by
  the user, and related test/build/lint verification. Apply project conventions
  and language-specific coding rules when relevant.
---

# CodeCraft

Implement only the requested change, using the project's established design and code conventions.

## Principles

- Follow KISS and YAGNI. Prefer fewer components and states, straightforward debugging, and maintainable code. Explain any necessary complexity and trade-offs.
- Prioritize the main flow and common cases; address edge cases when reasonably likely or high-impact.
- Do not invent second- or third-order requirements from hypothetical scenarios or introduce abstractions for speculative future needs.
- Reuse existing structures, APIs, libraries, frameworks, and terminology. Prefer localized changes over unrelated refactoring.
- Apply current rules to new or substantially changed code; do not restyle unrelated code or create noisy formatting-only diffs.

## Language Conventions

- Use Traditional Chinese for responses, explanations, comments, and work records unless the project or user explicitly specifies otherwise.
- Use English for code identifiers; retain established technical names and project terminology. Name variables, parameters, fields, and named return values in the singular, including collections.
- Comments should explain reasons, constraints, and non-obvious intent, rather than narrating each line.
- Where suitable, use `itor` as a general iteration variable and `k, v` for map key/value iteration.
- Do not edit generated code directly; update its source or generation process.
- **For Go changes, read `references/go.md`. For C# changes, read `references/csharp.md`.** Load only the language references relevant to this task. Follow more specific project rules where they differ.

## Workflow

1. **Inspect:** Read relevant requirements, code, existing tests, and project instructions. Check the working tree before editing; preserve unrelated existing changes.
2. **Plan minimally:** Determine the smallest sound change. Do not expand public APIs merely to make testing easier.
3. **Implement:** Modify only relevant files and necessary dependent code. Keep unrelated formatting and ordering unchanged.
4. **Verify:** Run applicable existing tests, linters, builds, or checks for the change. Do not invent commands or claim unrun checks passed.
5. **Report:** Summarize the change, executed checks and results, failures or limitations, and unresolved issues.

## Verification and Safety

- If verification fails, distinguish failures caused by this change from pre-existing problems; do not fix unrelated problems just to obtain a passing result.
- If a test disagrees with a confirmed authoritative specification, use that specification to determine whether the test or implementation needs correction. Do not silently change requirements.
- Never overwrite, restore, or delete another person's unrelated work.
- Keep temporary scripts and artifacts grouped in the project's designated temporary directory. If none exists, use a task-specific temporary location only when needed; clean up only artifacts created for this task. Do not assume a directory is Git-ignored.
- Do not commit, push, rebase, reset, or merge unless explicitly authorized.
- If the user requests analysis only, do not modify files.
