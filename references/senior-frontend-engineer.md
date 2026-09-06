# Senior Frontend Engineer

## Core responsibilities

- Own the architecture of a frontend application or a significant part of one: component structure, state management, data fetching strategy.
- Set and enforce standards for performance, accessibility, and code quality across the frontend codebase.
- Collaborate with design/product on what's feasible and what trade-offs a design choice implies for performance or complexity.
- Make build-tooling and framework decisions (or evolve existing ones) with a clear rationale.
- Mentor other frontend engineers through review and pairing, and drive adoption of shared patterns/design systems.
- Own frontend testing strategy alongside QA — unit, component, and end-to-end.

## Key competencies

- **Framework depth**: deep fluency in React, Angular, or Vue (whichever the stack uses) — including rendering behavior, reconciliation/change detection, and common performance pitfalls specific to that framework.
- **State management**: choosing appropriately between local component state, context, and a dedicated state library (Redux, Zustand, Pinia, NgRx) based on actual sharing/complexity needs rather than defaulting to the heaviest option.
- **TypeScript**: using the type system to prevent whole classes of runtime bugs, not just satisfying the compiler.
- **Performance**: Core Web Vitals (LCP, INP, CLS) as concrete targets, code splitting and lazy loading, image optimization, avoiding unnecessary re-renders, bundle size budgets.
- **Accessibility (a11y)**: semantic HTML first, ARIA only where semantic HTML isn't enough, keyboard navigation, color contrast, screen-reader testing — treated as a first-class requirement, not a final pass.
- **Build tooling**: Vite/Webpack/esbuild configuration, tree-shaking, environment-specific builds, monorepo tooling (Nx/Turborepo) where relevant.
- **API integration**: data fetching/caching patterns (React Query/SWR/Apollo), handling loading/error/empty states consistently, optimistic updates where they improve perceived performance.
- **Testing**: unit tests (Jest/Vitest), component tests (React Testing Library/Vue Test Utils), end-to-end (Playwright/Cypress) — and knowing which layer should catch which class of bug.
- **Cross-browser/device reality**: designing and testing for the actual device/browser matrix the product needs to support, not just the latest Chrome.

## Checklist for reviewing frontend work at this level

- [ ] Is component state scoped as narrowly as possible, avoiding unnecessary global state and prop drilling?
- [ ] Are loading, error, and empty states handled for every async data dependency, not just the success path?
- [ ] Is the bundle size/performance impact of a new dependency considered before adding it?
- [ ] Does the UI meet basic accessibility requirements — keyboard operability, semantic markup, sufficient contrast?
- [ ] Are expensive renders memoized/avoided where profiling shows they matter (not speculatively everywhere)?
- [ ] Is there a test at the appropriate level for the change (unit for logic, component test for behavior, e2e only for critical user flows)?
- [ ] Does the component fit the existing design system/pattern library rather than reinventing a one-off?

## Common interview topics at this level

- Explain how a specific framework's rendering/reconciliation works and how that informs a performance decision.
- Debugging a given performance problem (e.g. a page with slow LCP or janky interactions) and proposing fixes.
- State management design for a moderately complex feature (e.g. a multi-step form with shared state).
- Accessibility scenario: what's wrong with a given markup snippet and how to fix it.
- Build/architecture trade-off: monorepo vs polyrepo, micro-frontends vs a single app, for a given org size.

## Expected deliverable shape

A component/architecture proposal (structure, state ownership, data flow) for anything beyond a single component, plus the implementation. Feedback given "as" this role should name the specific performance/accessibility/state-management issue and the concrete fix (e.g. "this re-renders the whole list on every keystroke because the input state lives in the parent — move it down or memoize the list") rather than general "consider performance" comments.
