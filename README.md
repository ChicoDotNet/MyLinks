# MyLinks

[![Check links](https://github.com/ChicoDotNet/MyLinks/actions/workflows/check-links.yml/badge.svg)](https://github.com/ChicoDotNet/MyLinks/actions/workflows/check-links.yml)

A compact, opinionated collection of links I use to make development and troubleshooting faster.

> Last reviewed: 2026-07-15

## Cloud service health

- [AWS Health Dashboard](https://health.aws.amazon.com/health/status)
- [Microsoft Azure status](https://azure.status.microsoft/en-us/status/)
- [Google Cloud service health](https://status.cloud.google.com/)
- [GitHub status](https://www.githubstatus.com/)

## Learning

- [Microsoft Certified: Azure AI Engineer Associate](https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-engineer/)

## .NET and architecture

- [.NET documentation](https://learn.microsoft.com/en-us/dotnet/)
- [ASP.NET Core documentation](https://learn.microsoft.com/en-us/aspnet/core/)
- [Azure Architecture Center](https://learn.microsoft.com/en-us/azure/architecture/)

## Identity and security

- [Microsoft identity platform documentation](https://learn.microsoft.com/en-us/entra/identity-platform/)
- [Angular SPA authentication tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-apps-angular-prepare-app)
- [OAuth 2.0 scopes and OpenID Connect permissions](https://learn.microsoft.com/en-us/entra/identity-platform/scopes-oidc)

## Localization

- [Globalization and localization in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/localization/)

## File transfer

- [SSH.NET](https://github.com/sshnet/SSH.NET)

## Media

- [FFmpeg downloads](https://ffmpeg.org/download.html)

## Diagrams and markup

- [Mermaid documentation](https://mermaid.js.org/)

## Repository workflow

- `main` is the only long-lived branch.
- Use a short-lived branch for each change, such as `docs/add-link` or `chore/refresh-links`.
- Open a pull request before updating `main`.
- Delete the source branch after the pull request is merged.

## Maintenance rules

- Prefer official or primary sources over third-party tutorials.
- Prefer HTTPS links and pages that are actively maintained.
- Replace outdated links instead of keeping duplicate legacy references.
- Let the automated link checker detect link rot on pull requests and on a monthly schedule.
