# React + TypeScript + Vite

**Recommended** for modern web applications when the team wants React's ecosystem with a small, explicit client architecture.

## Start here

- [React Quick Start](https://react.dev/learn)
- [Vite Getting Started](https://vite.dev/guide/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [React Developer Tools](https://react.dev/learn/react-developer-tools)

Create a TypeScript project with the official Vite React template rather than copying an old starter repository:

```bash
npm create vite@latest my-app -- --template react-ts
```

## Authentication

- [Microsoft Entra React SPA tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-react-prepare-app)
- [MSAL React documentation](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react)
- [MSAL Browser documentation](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser)
- [Microsoft identity platform code samples](https://learn.microsoft.com/en-us/entra/identity-platform/sample-v2-code)

The Microsoft tutorial explains the MSAL integration, including workforce and external tenants. Scaffold new applications with Vite + TypeScript and adapt the tutorial's authentication configuration instead of adopting its project generator blindly.

See the repository recipe: [React + Vite + Microsoft Entra SPA](../../recipes/react-vite-entra-spa.md).

## UI

- [Fluent UI React v9](https://react.fluentui.dev/)
- [Fluent 2 design system](https://fluent2.microsoft.design/)
- [Bootstrap documentation](https://getbootstrap.com/docs/5.3/getting-started/introduction/)
- [React Bootstrap](https://react-bootstrap.github.io/)

Use Fluent UI for product interfaces aligned with Microsoft 365 or Fluent design. Use Bootstrap when speed, familiar responsive primitives, and broad template availability matter more than a distinctive design system.

## Routing and server state

- [React Router](https://reactrouter.com/)
- [TanStack Query](https://tanstack.com/query/latest/docs/framework/react/overview)

Avoid adding a global state library by default. Start with component state, context for stable application services, and a server-state library only when remote-data synchronization becomes material.

## Forms and validation

- [React Hook Form](https://react-hook-form.com/get-started)
- [Zod](https://zod.dev/)

Prefer shared API schemas or generated clients when possible so validation rules do not drift independently across frontend and backend.

## Testing

- [Vitest](https://vitest.dev/guide/)
- [Testing Library for React](https://testing-library.com/docs/react-testing-library/intro/)
- [Playwright](https://playwright.dev/docs/intro)

Recommended minimum:

- Vitest for fast unit tests.
- Testing Library for behavior-oriented component tests.
- Playwright for critical end-to-end journeys.

## Quality and delivery

- [ESLint](https://eslint.org/docs/latest/use/getting-started)
- [Prettier](https://prettier.io/docs/)
- [Vite environment variables](https://vite.dev/guide/env-and-mode)
- [Vite production build](https://vite.dev/guide/build)

Never place secrets in client-side environment variables. Values bundled into a SPA must be treated as public configuration.

## When not to choose this route

Consider Angular when strong framework conventions, dependency injection, forms, routing, and an integrated enterprise structure are more valuable than ecosystem flexibility. Consider server-rendered approaches when discoverability, first-load performance, or server-owned rendering is central to the product.
