# ReactJS Review Checklist

## 1. Hooks & State Management
- [ ] **Dependency Arrays:** Are `useEffect`, `useMemo`, and `useCallback` dependency arrays complete and accurate?
- [ ] **State Locality:** Is state kept as local as possible? Avoid "props drilling" where `useContext` or a state manager is better.
- [ ] **State Updates:** Are state updates based on previous state using the functional form `setState(prev => ...)` when necessary?
- [ ] **Cleanup:** Do effects have necessary cleanup functions (e.g., clearing timers, unsubscribing)?

## 2. Performance
- [ ] **Unnecessary Re-renders:** Are expensive components wrapped in `React.memo`? Are functions/objects passed as props stabilized with `useCallback` or `useMemo`?
- [ ] **Keys:** Are stable, unique keys used for list items (avoid using array index as a key)?
- [ ] **Lazy Loading:** Are large components or routes using `React.lazy` and `Suspense`?

## 3. Components & Props
- [ ] **Composition:** Is the component too large? Suggest breaking it down into smaller, reusable components.
- [ ] **Prop Types/TypeScript:** Are props strictly typed?
- [ ] **Naming:** Are components named using PascalCase and handlers using `handle` prefix (e.g., `handleClick`)?

## 4. Styling & Accessibility
- [ ] **Semantic HTML:** Are semantic tags used instead of generic `div`s?
- [ ] **ARIA:** Are necessary ARIA attributes provided for custom UI components?
- [ ] **Clarity:** Is styling (CSS-in-JS, Tailwind, CSS Modules) organized and maintainable?
