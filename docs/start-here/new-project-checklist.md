# New-project checklist

Use this checklist before the first feature is implemented. Skip an item only as an explicit decision.

## 1. Product and scope

- Define the user, problem, measurable outcome, and first vertical slice.
- Decide whether the deliverable is a prototype, PoC, MVP, internal tool, or production system.
- Define what is intentionally out of scope.
- Record the owner, expected lifetime, budget ceiling, and support model.

## 2. Application shape

- Choose web, API, mobile, desktop, background worker, CLI, embedded, or a combination.
- Choose the preferred golden path from the repository root.
- Identify offline, real-time, multimedia, AI, and device-integration requirements.
- Decide whether a modular monolith is sufficient before introducing distributed services.

## 3. Repository

- Create `README.md`, `.gitignore`, license, and contribution rules.
- Protect `main` and require a pull request.
- Enable dependency and secret scanning when available.
- Add architecture decision records for material choices.
- Define branch, commit, versioning, and release conventions.

## 4. Developer experience

- Pin or document runtime and SDK versions.
- Provide one command to restore dependencies.
- Provide one command to start the application locally.
- Provide one command to run all automated checks.
- Add sample environment variables without committing secrets.
- Decide whether Dev Containers, Docker Compose, or local emulators add enough value.

## 5. Identity and authorization

- Decide whether users are workforce, customer, partner, device, service, or anonymous identities.
- Register applications and redirect URIs for each environment.
- Define delegated scopes, application permissions, roles, and administrative consent.
- Separate authentication from authorization rules.
- Define token storage, logout, session expiration, and account recovery behavior.

## 6. Data

- Choose the system of record and ownership boundary for each dataset.
- Define migrations, seed data, retention, deletion, and backup policies.
- Classify sensitive data and personally identifiable information.
- Decide whether cache, object storage, search, vectors, or event storage are required.
- Add concurrency and idempotency rules for write operations.

## 7. API and integration

- Define the API contract before coupling clients to implementation details.
- Add OpenAPI for HTTP APIs when applicable.
- Define pagination, errors, validation, versioning, rate limits, and idempotency.
- Choose webhooks, queues, streaming, WebSockets, SignalR, or gRPC only when needed.
- Document external dependencies, failure modes, timeouts, retries, and circuit breakers.

## 8. Security

- Keep secrets in a managed secret store or protected local user-secrets facility.
- Define CORS, CSP, HTTPS, headers, input validation, and file-upload constraints.
- Review the relevant [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/).
- Generate a software bill of materials when the delivery context requires it.
- Define dependency-update and vulnerability-response responsibilities.

## 9. Quality

- Add formatting, linting, type checking, and unit tests.
- Add integration tests around databases, queues, storage, and identity boundaries.
- Add end-to-end tests for the first critical user journey.
- Include accessibility checks for user interfaces.
- Define performance budgets and load-test only the paths that justify it.

## 10. Observability and operations

- Add structured logs with correlation identifiers.
- Add metrics, distributed traces, health checks, and dependency checks as appropriate.
- Define alert ownership and meaningful service-level indicators.
- Document backup, restore, rollback, and incident procedures.
- Estimate cloud and third-party costs before production deployment.

## 11. Delivery

- Add continuous integration for every pull request.
- Separate build artifacts from deployment configuration.
- Use infrastructure as code for repeatable environments when practical.
- Define dev, test, staging, and production boundaries.
- Add an explicit release, rollback, and database-migration strategy.

## Definition of ready

A project is ready for feature work when a new contributor can clone it, configure documented variables, run it, execute its checks, and understand the first vertical slice without private oral instructions.
