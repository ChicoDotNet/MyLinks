# Application foundations

These capabilities apply across frontend, backend, mobile, desktop, AI, and multimedia applications. Make them explicit at project creation instead of adding them only after the first incident.

## Identity and authorization

- [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/)
- [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/)
- [OAuth 2.0 scopes and OpenID Connect permissions](https://learn.microsoft.com/en-us/entra/identity-platform/scopes-oidc)
- [OAuth 2.0 Security Best Current Practice](https://datatracker.ietf.org/doc/html/rfc9700)
- [OpenID Connect specifications](https://openid.net/developers/specs/)

Decide first who the identities are: workforce users, customers, partners, services, devices, or anonymous visitors. Model roles and permissions around business operations rather than screen names.

## API design

- [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [REST API guidelines from Microsoft](https://github.com/microsoft/api-guidelines)
- [Problem Details for HTTP APIs](https://www.rfc-editor.org/info/rfc9457)
- [gRPC documentation](https://grpc.io/docs/)
- [AsyncAPI specification](https://www.asyncapi.com/docs/reference/specification/v3.1.0)

Define errors, validation, pagination, concurrency, idempotency, versioning, rate limits, and deprecation behavior before clients depend on accidental implementation details.

## Data and storage

- [Azure SQL documentation](https://learn.microsoft.com/en-us/azure/azure-sql/?view=azuresql)
- [PostgreSQL documentation](https://www.postgresql.org/docs/)
- [Azure Storage documentation](https://learn.microsoft.com/en-us/azure/storage/)
- [Redis documentation](https://redis.io/docs/latest/)
- [Azure AI Search documentation](https://learn.microsoft.com/en-us/azure/search/)

Choose a system of record for each concept. Add caches, search indexes, vector stores, analytics copies, and event streams as derived stores with defined synchronization and recovery behavior.

## Security

- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [OWASP Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [GitHub secret scanning](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning)
- [GitHub dependency review](https://docs.github.com/en/code-security/concepts/supply-chain-security/dependency-review)
- [Azure Key Vault documentation](https://learn.microsoft.com/en-us/azure/key-vault/)

Minimum expectations:

- No secrets in source control or client bundles.
- Least-privilege identities for workloads and people.
- Validation at every trust boundary.
- Safe file-upload limits and content inspection.
- Dependency and vulnerability monitoring.
- Threat modeling for high-impact operations and sensitive data.

## Testing

- [Playwright](https://playwright.dev/docs/intro)
- [Vitest](https://vitest.dev/guide/)
- [pytest](https://docs.pytest.org/en/stable/getting-started.html)
- [.NET testing](https://learn.microsoft.com/en-us/dotnet/core/testing/)
- [k6 load testing](https://grafana.com/docs/k6/latest/)
- [Testcontainers](https://testcontainers.com/)

Use the smallest test level that proves the behavior, but include realistic integration tests for databases, queues, object storage, identity, and external protocols where mocks would hide material differences.

## Observability

- [OpenTelemetry documentation source](https://github.com/open-telemetry/opentelemetry.io)
- [OpenTelemetry semantic conventions](https://opentelemetry.io/docs/specs/semconv/)
- [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/)
- [Application Insights](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)

Correlate logs, metrics, and traces. Define service-level indicators around user outcomes and dependency health, not only CPU and memory.

Do not log credentials, tokens, payment data, full identity documents, or unrestricted AI prompts and responses by default.

## Resilience

- [Azure Architecture Center reliability guidance](https://learn.microsoft.com/en-us/azure/well-architected/reliability/)
- [Cloud Design Patterns](https://learn.microsoft.com/en-us/azure/architecture/patterns/)

For each external dependency define:

- Timeout.
- Cancellation.
- Retry eligibility and limit.
- Idempotency.
- Circuit-breaking or degradation behavior.
- Observability.
- Recovery and reconciliation.

Retries without timeouts and idempotency can amplify incidents.

## DevOps and infrastructure

- [GitHub Actions](https://docs.github.com/en/actions)
- [Docker Get Started](https://docs.docker.com/get-started/)
- [Azure Developer CLI](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/)
- [Bicep documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/)
- [Terraform documentation](https://developer.hashicorp.com/terraform/docs)
- [GitHub environments](https://docs.github.com/en/actions/how-tos/deploy/configure-and-manage-deployments/manage-environments)

Create immutable build artifacts and promote them through environments. Keep environment-specific values outside the artifact. Prefer workload identity federation or managed identity over long-lived deployment secrets.

## Configuration and feature management

- [Twelve-Factor App configuration](https://12factor.net/config)
- [Azure App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/)
- [OpenFeature](https://openfeature.dev/docs/reference/intro/)

Separate secrets from non-secret configuration. Use feature flags for controlled release and operational switches, not as permanent substitutes for a coherent domain model.

## Documentation

Each production repository should contain:

- Purpose and user outcomes.
- Local setup and one-command checks.
- Architecture and main data flows.
- Environment variables and external dependencies.
- Deployment and rollback.
- Backup and restore.
- Security assumptions.
- Operational dashboards and alerts.
- Known limitations and technical debt.
- Architecture decision records for material choices.

Use [Mermaid](https://mermaid.js.org/) for diagrams that benefit from version control and text review.
