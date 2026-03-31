---
name: react-test-engineer
description: "Writes and improves React component tests using Vitest and React Testing Library. Configures test setup, creates user-centric tests with role-based queries, mocks modules and hooks, tests async data loading, and runs accessibility audits with vitest-axe. Use when the user asks to write, debug, or improve tests for React components, or mentions React Testing Library, RTL, Vitest, component testing, or test coverage."
---

# React Testing Engineer (Vitest + RTL)

## Core Principles

1. **Test behavior, not implementation.** Test what users see and interact with — not state, methods, or lifecycle hooks. Refactoring internals should never break tests.
2. **Query priority:** `getByRole` (preferred) > `getByLabelText` > `getByPlaceholderText` > `getByText` > `getByDisplayValue` > `getByAltText` > `getByTitle` > `getByTestId` (last resort).
3. **Async:** Use `findBy*` for elements that appear asynchronously. Use `waitFor` only for non-element assertions.
4. **User events:** Always use `@testing-library/user-event` (not `fireEvent`). Start each test with `const user = userEvent.setup()`.
5. **Accessibility:** Run `vitest-axe` checks on all new components.

## Setup & Configuration

### Dependencies

```bash
npm install -D vitest jsdom @testing-library/react @testing-library/jest-dom @testing-library/user-event vitest-axe
```

### Vitest Config (`vite.config.ts` or `vitest.config.ts`)

```typescript
/// <reference types="vitest" />
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: 'jsdom',
    setupFiles: './src/test/setup.ts',
    css: true,
  },
});
```

### Setup File (`./src/test/setup.ts`)

Use the side-effect import — do NOT also call `expect.extend(matchers)` manually.

```typescript
import '@testing-library/jest-dom';
import { cleanup } from '@testing-library/react';
import { afterEach } from 'vitest';

afterEach(() => { cleanup(); });
```

## Custom Render with Providers

Wrap tests in app-level providers (Theme, Auth, Router, etc.):

```typescript
// src/test/test-utils.tsx
import { render, RenderOptions } from '@testing-library/react';
import { ReactElement, ReactNode } from 'react';
import { ThemeProvider } from 'my-theme-lib';
import { AuthProvider } from '../context/auth';

const AllTheProviders = ({ children }: { children: ReactNode }) => (
  <ThemeProvider theme="light">
    <AuthProvider>{children}</AuthProvider>
  </ThemeProvider>
);

const customRender = (ui: ReactElement, options?: Omit<RenderOptions, 'wrapper'>) =>
  render(ui, { wrapper: AllTheProviders, ...options });

export * from '@testing-library/react';
export { customRender as render };
```

## Common Patterns

### Form Submission

```typescript
import { render, screen } from './test-utils';
import userEvent from '@testing-library/user-event';
import { vi } from 'vitest';
import { LoginForm } from '../components/LoginForm';

test('submits form with valid data', async () => {
  const handleSubmit = vi.fn();
  const user = userEvent.setup();
  render(<LoginForm onSubmit={handleSubmit} />);

  await user.type(screen.getByLabelText(/username/i), 'john_doe');
  await user.type(screen.getByLabelText(/password/i), 'secret');
  await user.click(screen.getByRole('button', { name: /log in/i }));

  expect(handleSubmit).toHaveBeenCalledWith({ username: 'john_doe', password: 'secret' });
});
```

### Async Data Loading

```typescript
import { render, screen } from '@testing-library/react';
import { UserList } from '../components/UserList';

test('displays users after loading', async () => {
  render(<UserList />);
  expect(screen.getByRole('status', { name: /loading/i })).toBeInTheDocument();

  const userItem = await screen.findByText(/Alice/i);
  expect(userItem).toBeInTheDocument();
  expect(screen.queryByRole('status', { name: /loading/i })).not.toBeInTheDocument();
});
```

### Module Mocking

```typescript
import { render, screen } from '@testing-library/react';
import { vi } from 'vitest';
import { UserProfile } from '../components/UserProfile';
import * as authHook from '../hooks/useAuth';

vi.mock('../hooks/useAuth');

test('renders user name when authenticated', () => {
  vi.spyOn(authHook, 'useAuth').mockReturnValue({
    user: { name: 'Alice' },
    isAuthenticated: true,
  });
  render(<UserProfile />);
  expect(screen.getByText(/Alice/i)).toBeInTheDocument();
});
```

### Custom Hooks

```typescript
import { renderHook, act } from '@testing-library/react';
import { useCounter } from '../hooks/useCounter';

test('should increment counter', () => {
  const { result } = renderHook(() => useCounter());
  act(() => { result.current.increment(); });
  expect(result.current.count).toBe(1);
});
```

### Accessibility Audit

```typescript
import { render } from '@testing-library/react';
import { axe, toHaveNoViolations } from 'vitest-axe';
import { expect } from 'vitest';
import { LoginForm } from '../components/LoginForm';

expect.extend(toHaveNoViolations);

test('LoginForm has no accessibility violations', async () => {
  const { container } = render(<LoginForm onSubmit={() => {}} />);
  const results = await axe(container);
  expect(results).toHaveNoViolations();
});
```

## Checklist

- [ ] Use `render` from RTL (never `shallow`).
- [ ] Arrange-Act-Assert structure in every test.
- [ ] Wait for async UI to settle before asserting.
- [ ] Use `vi.fn()` for stubs; `vi.mock()` for modules.
- [ ] Run axe checks on new components.

## Debugging

- `screen.debug()` — prints current DOM.
- `logRoles(container)` — shows ARIA roles (useful when `getByRole` fails).
- `npx vitest --ui` — visual browser-based test dashboard.