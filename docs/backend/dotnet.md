# .NET and ASP.NET Core

**Recommended** for enterprise APIs, web applications, workers, integrations, and cloud services where strong typing, mature tooling, performance, and the Microsoft ecosystem are material advantages.

## Start here

- [.NET documentation](https://learn.microsoft.com/en-us/dotnet/)
- [.NET releases and support](https://learn.microsoft.com/en-us/dotnet/core/releases-and-support)
- [ASP.NET Core documentation](https://learn.microsoft.com/en-us/aspnet/core/)
- [.NET application architecture guides](https://learn.microsoft.com/en-us/dotnet/architecture/)
- [.NET CLI overview](https://learn.microsoft.com/en-us/dotnet/core/tools/)

Prefer a currently supported LTS or STS release according to the application's maintenance horizon. Pin the SDK with `global.json` when reproducibility across machines and CI matters.

## Web APIs

- [Minimal APIs](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis/)
- [Controller-based APIs](https://learn.microsoft.com/en-us/aspnet/core/web-api/)
- [OpenAPI support](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/openapi/overview)
- [HTTP client factory](https://learn.microsoft.com/en-us/dotnet/core/extensions/httpclient-factory)
- [Rate limiting](https://learn.microsoft.com/en-us/aspnet/core/performance/rate-limit)

Use Minimal APIs for compact services and vertical slices. Use controllers when filters, conventions, large endpoint sets, or team familiarity make their structure advantageous. Do not treat either style as an architectural boundary by itself.

## Data

- [Entity Framework Core](https://learn.microsoft.com/en-us/ef/core/)
- [EF Core migrations](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/)
- [ADO.NET](https://learn.microsoft.com/en-us/dotnet/framework/data/adonet/)
- [Azure SQL documentation](https://learn.microsoft.com/en-us/azure/azure-sql/)
- [Azure Blob Storage for .NET](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-dotnet)

Keep migrations versioned with the application. Review generated migrations before applying them and define how production migrations are coordinated with application rollout.

## Identity and security

- [ASP.NET Core security](https://learn.microsoft.com/en-us/aspnet/core/security/)
- [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/)
- [Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msal/dotnet/microsoft-identity-web/)
- [ASP.NET Core authorization](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/introduction)
- [Secret Manager](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets)
- [Azure Key Vault configuration provider](https://learn.microsoft.com/en-us/aspnet/core/security/key-vault-configuration)

Authorize every protected operation in the backend. Client-side route guards and hidden buttons are usability features, not security boundaries.

## Communication and background work

- [SignalR](https://learn.microsoft.com/en-us/aspnet/core/signalr/introduction)
- [gRPC for .NET](https://learn.microsoft.com/en-us/aspnet/core/grpc/)
- [Worker services](https://learn.microsoft.com/en-us/dotnet/core/extensions/workers)
- [Hosted services](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services)

Use queues or durable orchestration for work that must survive process restarts. A fire-and-forget task inside an HTTP request is not a durable job system.

## Resilience and observability

- [.NET resilience](https://learn.microsoft.com/en-us/dotnet/core/resilience/)
- [OpenTelemetry with .NET](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/observability-with-otel)
- [ASP.NET Core logging](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/logging/)
- [Health checks](https://learn.microsoft.com/en-us/aspnet/core/host-and-deploy/health-checks)

Add timeouts first, then bounded retries for transient operations. Include correlation identifiers and avoid logging tokens, secrets, or unnecessary personal data.

## Testing

- [.NET testing overview](https://learn.microsoft.com/en-us/dotnet/core/testing/)
- [Integration tests in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests)
- [Playwright for .NET](https://playwright.dev/dotnet/docs/intro)
- [Testcontainers for .NET](https://dotnet.testcontainers.org/)

Prefer integration tests against realistic dependencies for persistence, queues, and identity boundaries. Mocking every infrastructure interface can produce tests that prove only the mocks agree with the implementation.

## Localization

- [Globalization and localization in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/localization/)

## Deployment

- [Containerize a .NET application](https://learn.microsoft.com/en-us/dotnet/core/docker/build-container)
- [Azure App Service documentation](https://learn.microsoft.com/en-us/azure/app-service/)
- [Azure Container Apps documentation](https://learn.microsoft.com/en-us/azure/container-apps/)
- [Azure Developer CLI](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/)

## AI in .NET

See [Modern AI](../ai/modern-ai.md) for Microsoft.Extensions.AI, Semantic Kernel, OpenAI, Microsoft Foundry, ML.NET, and ONNX Runtime.
