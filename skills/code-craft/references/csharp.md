# C# Conventions

Apply these personal/project conventions to new or substantially modified C# code. More specific project rules take precedence.

- For `bool` expressions, test true directly (`if (ready) { ... }`), not with `== true`.
- Test false explicitly (`if (ready == false) { ... }`), not with a negation (`if (!ready) { ... }`).
- Use closing comments only when they meaningfully identify a control-flow block; do not add them to the end of a method or function.

These are deliberate conventions, not claims about universal C# style. Do not restyle unrelated existing code.
