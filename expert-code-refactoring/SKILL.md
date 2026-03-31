---
name: expert-code-refactoring
description: "Refactors Java, JavaScript, and React codebases by extracting methods, reducing coupling, applying design patterns (Factory, Strategy, Observer), eliminating duplication, and simplifying complex conditionals — all while keeping tests green. Use when the user asks to refactor code, improve code structure, apply design patterns, reduce technical debt, clean up code smells, restructure modules, or simplify complex Java/JavaScript/React code."
---

# Expert Code Refactoring

## Workflow

1. **Analyze Context:** Read the target file and its tests. Map dependencies and callers.
2. **Verify Baseline:** Run existing tests — do not proceed until they pass.
3. **Identify Smells:** Scan for long methods, deep nesting, duplication, tight coupling (see table below).
4. **Plan Transformations:** Choose the smallest refactoring that removes the smell. Prefer one pattern per commit.
5. **Apply & Re-verify:** Make the change, run tests. If tests fail, **revert the last step and try a smaller transformation**.
6. **Repeat:** Continue until the target smells are resolved or the user's goal is met.

## Clean Code Principles

- Rename to reveal intent — no abbreviations.
- AHA (Avoid Hasty Abstractions): only abstract when duplication is clear and the abstraction simplifies the code.
- Keep functions small with few parameters (use objects/records when > 3).
- Max 2–3 nesting levels; use early returns for the happy path.

## Refactoring for Testability

- **Dependency Injection:** Replace hardcoded instances/static calls with constructor or parameter injection.
- **Interface Segregation:** Extract smaller interfaces when only one method is consumed.
- **Pure Functions:** Move business logic into pure functions for trivial unit testing.
- **Seams for Mocking:** Identify boundaries (DB, Network, Clock) where mocks can be injected.

## Legacy Code Techniques

- **Characterization Tests:** Write "Golden Master" tests capturing current behavior *before* changing anything.
- **Sprout Method:** Add new logic in a clean method; call it from the legacy one.
- **Wrap Method:** Create a new method with the same signature that calls the old one and adds new behavior.
- **Extract and Override:** Isolate untestable static calls in a protected method overridable in test subclasses.

## Code Smells Quick Reference

| Smell | Refactoring |
| :--- | :--- |
| Magic Literals | Extract Constant / Enum |
| Long Method | Extract Method |
| Large Class | Extract Class / Interface |
| Feature Envy | Move Method |
| Primitive Obsession | Introduce Value Object |
| Shotgun Surgery | Move Field / Inline Class |

## Language-Specific Guidance

### Java
- Prefer `record` (14+), `sealed` classes (17+), switch pattern matching.
- Replace loops with `Stream`; eliminate null checks with `Optional`.
- Immutable collections (`List.of`, `Map.of`); try-with-resources for I/O.

### JavaScript / TypeScript
- `const` by default; destructuring, spread/rest, arrow functions.
- TypeScript: discriminated unions, utility types (`Pick`, `Omit`), custom type guards.
- Zod (or similar) for runtime validation at API/IO boundaries.
- `Promise.all` for concurrency; avoid sequential `await` in loops.

### React
- Decompose large components; extract logic into custom hooks.
- Keep state local (Principle of Least Privilege); avoid prop drilling via Context or Composition.
- `useMemo`/`useCallback` for stable references in memoized children.

## Constraints

- Never change public APIs or interfaces without explicit user permission.
- Always maintain or improve test coverage.
- Follow the project's existing linting and formatting rules.
- Never hardcode secrets — use environment variables.
