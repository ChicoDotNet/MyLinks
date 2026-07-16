# Angular

**Recommended alternative** for enterprise web applications that benefit from strong conventions, an integrated toolchain, dependency injection, routing, forms, and a consistent team structure.

## Start here

- [Angular documentation](https://angular.dev/)
- [Learn Angular](https://angular.dev/tutorials/learn-angular)
- [Angular CLI](https://angular.dev/tools/cli)
- [Angular style guide](https://angular.dev/style-guide)

Create a new project through the current CLI rather than copying an old application:

```bash
npx @angular/cli new my-app
```

## Architecture

- [Components](https://angular.dev/guide/components)
- [Signals](https://angular.dev/guide/signals)
- [Dependency injection](https://angular.dev/guide/di)
- [Routing](https://angular.dev/guide/routing)
- [HTTP client](https://angular.dev/guide/http)
- [Reactive forms](https://angular.dev/guide/forms/reactive-forms)

Prefer standalone components and current Angular patterns. Treat NgModules as an interoperability or legacy-maintenance concern unless a dependency genuinely requires them.

## Authentication

- [Microsoft Entra Angular SPA tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-apps-angular-prepare-app)
- [MSAL Angular](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-angular)
- [MSAL Browser](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser)
- [Microsoft identity platform code samples](https://learn.microsoft.com/en-us/entra/identity-platform/sample-v2-code)

Keep route visibility, token acquisition, and backend authorization as separate concerns. Hiding a route in the browser is not an authorization control.

## UI

- [Angular Material](https://material.angular.dev/)
- [Fluent UI Web Components](https://learn.microsoft.com/en-us/fluent-ui/web-components/)
- [Bootstrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/)
- [ng-bootstrap](https://ng-bootstrap.github.io/)

Use a single primary component system per application. Mixing Material, Fluent, and Bootstrap components indiscriminately creates inconsistent interaction and accessibility behavior.

## State and reactive programming

- [RxJS](https://rxjs.dev/guide/overview)
- [Angular signals](https://angular.dev/guide/signals)

Use signals for local and derived application state. Use RxJS when representing asynchronous streams, cancellation, composition, or integrations that are naturally observable. Add a global store only after application complexity demonstrates the need.

## Testing

- [Angular testing guide](https://angular.dev/guide/testing)
- [Playwright](https://playwright.dev/docs/intro)

Recommended minimum:

- Unit and component tests for business behavior.
- HTTP integration tests around client services.
- Playwright for critical end-to-end journeys.

## Internationalization and accessibility

- [Angular internationalization](https://angular.dev/guide/i18n)
- [Angular accessibility](https://angular.dev/best-practices/a11y)

## When not to choose this route

Choose React when ecosystem flexibility, incremental adoption, or sharing skills with React Native is more important than framework-wide conventions. Avoid choosing Angular solely because it was used in an older internal project; select it because its structure benefits the current team and product.
