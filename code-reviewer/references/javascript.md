# JavaScript Review Checklist

## 1. Modern Syntax (ES6+)
- [ ] **Arrow Functions:** Are they used correctly, especially regarding lexical `this`?
- [ ] **Destructuring:** Is it used for cleaner access to object properties and array elements?
- [ ] **Template Literals:** Are they used instead of string concatenation?
- [ ] **Spread/Rest:** Are they used effectively for copying arrays/objects or handling variable arguments?

## 2. Asynchronous Programming
- [ ] **Promises/Async-Await:** Are all promises handled? Avoid "Promise hell."
- [ ] **Error Handling:** Are `try/catch` blocks used with `async/await`?
- [ ] **Parallelism:** Is `Promise.all()` or `Promise.allSettled()` used when multiple independent async tasks can run concurrently?

## 3. Scope and Types
- [ ] **Variable Declaration:** Use `const` by default, `let` only if reassignment is needed. Avoid `var`.
- [ ] **Equality:** Use strict equality (`===`) instead of loose equality (`==`).
- [ ] **Type Checking:** If not using TypeScript, are critical inputs type-checked?

## 4. Code Quality
- [ ] **Naming:** Use camelCase for variables and functions, PascalCase for classes.
- [ ] **Modularity:** Are functions small and focused on a single task?
- [ ] **Global Scope:** Avoid polluting the global namespace.
