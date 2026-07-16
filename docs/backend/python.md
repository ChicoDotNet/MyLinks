# Python and FastAPI

**Recommended** for AI-heavy services, automation, data processing, rapid APIs, and integrations where Python's ecosystem provides a decisive advantage.

## Start here

- [Python tutorial](https://docs.python.org/3/tutorial/)
- [Python standard library](https://docs.python.org/3/library/)
- [Python packaging user guide](https://packaging.python.org/en/latest/)
- [uv](https://docs.astral.sh/uv/)

Use a project-level virtual environment and lock dependencies. `uv` is the preferred route in this handbook because it can manage Python versions, environments, dependencies, scripts, and lockfiles through one fast tool.

```bash
uv init my-service
cd my-service
uv add fastapi --extra standard
```

## API stack

- [FastAPI tutorial](https://fastapi.tiangolo.com/tutorial/)
- [Pydantic documentation](https://pydantic.dev/docs/validation/latest/get-started/)
- [Uvicorn installation](https://uvicorn.dev/installation/)
- [Starlette](https://www.starlette.io/)

Use Pydantic models at system boundaries. Keep domain behavior out of route functions and avoid turning request models directly into persistence models when their lifecycles differ.

## Data

- [SQLAlchemy Unified Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/)
- [SQLAlchemy asyncio](https://docs.sqlalchemy.org/en/20/orm/extensions/asyncio.html)
- [Alembic tutorial](https://alembic.sqlalchemy.org/en/latest/tutorial.html)
- [PostgreSQL documentation](https://www.postgresql.org/docs/)

Use Alembic migrations as reviewed source code. Do not generate schema changes automatically in production at application startup.

## Type checking and quality

- [Python typing](https://docs.python.org/3/library/typing.html)
- [mypy](https://mypy.readthedocs.io/en/stable/getting_started.html)
- [Ruff](https://docs.astral.sh/ruff/)
- [pre-commit](https://pre-commit.com/)

Recommended minimum:

- Type annotations at public boundaries.
- Ruff for linting and formatting.
- A static type checker for business-critical services.
- Pre-commit or equivalent CI checks to keep local and remote quality rules aligned.

## Testing

- [pytest](https://docs.pytest.org/en/stable/getting-started.html)
- [FastAPI testing](https://fastapi.tiangolo.com/tutorial/testing/)
- [pytest-asyncio](https://pytest-asyncio.readthedocs.io/en/stable/)
- [Testcontainers for Python](https://testcontainers-python.readthedocs.io/en/latest/)

Use real database and service containers for the integration paths where SQL dialects, migrations, transactions, or broker behavior matter.

## Background work and workflows

- [Celery](https://docs.celeryq.dev/en/stable/getting-started/introduction.html)
- [Azure Functions Python developer guide](https://learn.microsoft.com/en-us/azure/azure-functions/functions-reference-python)

Do not execute durable work as an untracked background coroutine inside an HTTP process. Select a queue, function platform, or workflow engine when retries and recovery matter.

## Observability

- [OpenTelemetry Python](https://opentelemetry.io/docs/languages/python/)
- [Python logging](https://docs.python.org/3/howto/logging.html)

Use structured logs and propagate trace context across HTTP, queues, model calls, and databases.

## AI and data

- [OpenAI Python library](https://github.com/openai/openai-python)
- [Microsoft Foundry SDKs and tools](https://learn.microsoft.com/en-us/azure/foundry/how-to/develop/sdk-overview)
- [pandas](https://pandas.pydata.org/docs/getting_started/index.html)
- [scikit-learn](https://scikit-learn.org/stable/getting_started.html)
- [PyTorch tutorials](https://docs.pytorch.org/tutorials/)

See [Modern AI](../ai/modern-ai.md) for model integration, agents, embeddings, local inference, evaluation, and safety.

## When not to choose this route

Choose .NET when the service belongs primarily to a .NET enterprise estate and Python does not provide a material ecosystem advantage. Choose Rust when deterministic resource use, a small native binary, memory safety without garbage collection, or low-level multimedia and systems integration are central requirements.
