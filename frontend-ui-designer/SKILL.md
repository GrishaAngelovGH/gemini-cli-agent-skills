---
name: frontend-ui-designer
description: "Builds responsive layouts, implements component hierarchies, applies design tokens and theming, and ensures WCAG accessibility compliance for frontend UIs. Use when the user asks to design or implement UI components, page layouts, CSS/Tailwind styling, responsive design, dark mode, forms, navigation, empty states, or skeleton loading screens."
---

# Frontend UI Designer

## Design Workflow

When asked to design or implement a UI:

1. **Establish layout** — choose grid/flex structure, set container widths, apply 8pt spacing grid.
2. **Apply color palette** — 60-30-10 rule, semantic status colors, dark mode equivalents.
3. **Set typography** — font pairing, modular scale, line heights.
4. **Build components** — forms, empty states, skeletons, navigation patterns.
5. **Add interactions** — hover states, transitions (150–300ms), loading feedback.
6. **Validate accessibility** — keyboard nav, touch targets ≥44px, semantic HTML, ARIA labels, WCAG contrast.

## Visual Hierarchy

- Make CTAs most prominent via size, weight, and color.
- Use generous white space and proximity-based grouping.

## Color

- **60-30-10:** 60% neutral (backgrounds), 30% secondary (borders/text), 10% accent (CTAs).
- **Semantic:** Success #10B981, Error #EF4444, Warning #F59E0B, Info #3B82F6.
- **Dark mode:** Use Slate-800/900 (not pure black) for backgrounds.
- **Suggested palette:** Primary Indigo #6366F1, Surface #F8FAFC, Headings Slate-900 #0F172A, Body Slate-600 #475569.

## Typography

- Fonts: Inter, Geist, Roboto, or SF Pro Display — max 2 families.
- Scale (Major Third): H1 2.25rem bold, H2 1.875rem semi-bold, H3 1.5rem semi-bold, Body 1rem, Small 0.875rem.
- Line height: 1.5–1.6 for body, 1.2–1.3 for headings.

## Layout & Spacing

- **8pt grid:** 4, 8, 16, 24, 32, 48, 64px for all spacing.
- Standard container widths (max-w-7xl, max-w-5xl). Mobile-first with flex/grid.
- Bento-box grids for dashboards and data-heavy views.

## Modern Techniques

- **Shadows:** `box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);` over harsh borders.
- **Glassmorphism:** `background: rgba(255,255,255,0.7); backdrop-filter: blur(10px);` for overlays.
- **Borders:** `rounded-lg` (8px) or `rounded-xl` (12px).

## Component Patterns

- **Forms:** Single column, visible labels above inputs, inline validation, autocomplete attributes.
- **Empty states:** Illustration + explanation + primary action button.
- **Skeleton loading:** Shimmer screens mimicking final layout to reduce CLS.
- **Navigation:** Primary actions in thumb zone on mobile; support swipe gestures.

## Accessibility

- Keyboard: all interactive elements focusable with visible focus rings (`ring-2 ring-offset-2`).
- Touch targets: ≥44×44px (48×48px preferred).
- Semantic HTML (`<button>`, `<nav>`, `<main>`) + ARIA labels where needed.
- Immediate visual feedback for all actions (loading, success, error).

## Resources

- [Refactoring UI](https://www.refactoringui.com/), [Material 3](https://m3.material.io/), [Lucide Icons](https://lucide.dev/), [Adobe Color](https://color.adobe.com/), [Coolors](https://coolors.co/), [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/)
