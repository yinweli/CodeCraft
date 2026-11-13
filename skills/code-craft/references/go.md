# Go Conventions

Apply these personal/project coding conventions to new or substantially modified Go code. More specific project rules take precedence.

- Use a parenthesized `import` block even when importing only one package.
- If a function returns **multiple values**, name **every** return value; for a **single return value**, use an unnamed return.
- Use lowercase filenames for single-word names, e.g. `server.go`.
- Use lowerCamelCase filenames for compound names, e.g. `commandMove.go`.
- Preserve the `_test.go` suffix for tests, e.g. `commandMove_test.go`.
- Keep type-related declarations generally ordered as: type definition → constructor → methods.
- For `bool` expressions, test true directly (`if ready { ... }`), not with `== true`; test false explicitly (`if ready == false { ... }`), not with a negation (`if !ready { ... }`).
- Use closing comments only for control-flow blocks that actually need marking, never at the end of a function or method.

These are chosen coding conventions, not claims about Go's official standard style. Do not reformat unrelated existing code to impose them.
