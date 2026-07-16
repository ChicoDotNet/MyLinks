# Modern AI applications

Build AI as a product capability with explicit quality, cost, latency, safety, privacy, and fallback requirements. A successful API call is not evidence that an AI feature is production-ready.

## OpenAI platform

- [OpenAI developer quickstart](https://developers.openai.com/api/docs/quickstart)
- [Responses API migration guide](https://developers.openai.com/api/docs/guides/migrate-to-responses)
- [Model selection](https://developers.openai.com/api/docs/guides/model-selection)
- [Structured outputs](https://developers.openai.com/api/docs/guides/structured-outputs)
- [Function calling](https://developers.openai.com/api/docs/guides/function-calling)
- [Embeddings](https://developers.openai.com/api/docs/guides/embeddings)
- [Images and vision](https://developers.openai.com/api/docs/guides/images-vision)
- [Realtime and audio](https://developers.openai.com/api/docs/guides/realtime)
- [Production best practices](https://developers.openai.com/api/docs/guides/production-best-practices)
- [Safety best practices](https://developers.openai.com/api/docs/guides/safety-best-practices)
- [OpenAI Python SDK](https://github.com/openai/openai-python)
- [OpenAI .NET SDK](https://github.com/openai/openai-dotnet)
- [OpenAI JavaScript and TypeScript SDK](https://github.com/openai/openai-node)

Prefer the Responses API for new text, tool, retrieval, and multimodal workflows unless a specialized interface such as Realtime is required.

## Microsoft Foundry

- [What is Microsoft Foundry?](https://learn.microsoft.com/en-us/azure/foundry/what-is-foundry)
- [Microsoft Foundry documentation](https://learn.microsoft.com/en-us/azure/foundry/)
- [Foundry SDK overview](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/develop/sdk-overview)
- [Azure OpenAI documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/)
- [Responsible AI overview](https://learn.microsoft.com/en-us/azure/ai-services/responsible-use-of-ai-overview)

Use Foundry when Azure governance, managed identity, networking, model catalog access, evaluations, or enterprise operations justify the platform layer.

## AI in .NET

- [Microsoft.Extensions.AI](https://learn.microsoft.com/en-us/dotnet/ai/microsoft-extensions-ai)
- [Semantic Kernel](https://learn.microsoft.com/en-us/semantic-kernel/overview/)
- [.NET AI overview](https://learn.microsoft.com/en-us/dotnet/ai/)
- [ML.NET](https://dotnet.microsoft.com/en-us/apps/ai/ml-dotnet)
- [ONNX Runtime](https://onnxruntime.ai/docs/)

Preferred order:

1. Use an official provider SDK for a small, provider-specific integration.
2. Use Microsoft.Extensions.AI when common chat, embedding, middleware, telemetry, and provider abstraction are valuable.
3. Use Semantic Kernel when plugins, agent orchestration, process coordination, or its broader runtime features solve a demonstrated need.
4. Use ONNX Runtime or ML.NET for local or embedded inference when the model and deployment constraints support it.

## Agents and tools

- [OpenAI Agents SDK for Python](https://openai.github.io/openai-agents-python/)
- [OpenAI Agents SDK for JavaScript](https://openai.github.io/openai-agents-js/)
- [Model Context Protocol](https://modelcontextprotocol.io/introduction)
- [Semantic Kernel agents](https://learn.microsoft.com/en-us/semantic-kernel/frameworks/agent/)

Do not introduce multiple agents when one model call with deterministic application code and a small tool set can solve the workflow. Every tool must have a clear authorization boundary, input validation, timeout, audit trail, and idempotency strategy where relevant.

## Retrieval and knowledge

- [OpenAI retrieval guide](https://developers.openai.com/api/docs/guides/retrieval)
- [Azure AI Search documentation](https://learn.microsoft.com/en-us/azure/search/)
- [PostgreSQL pgvector](https://github.com/pgvector/pgvector)

Before implementing retrieval-augmented generation, define:

- Which source is authoritative.
- How documents are segmented and versioned.
- How permissions are preserved through retrieval.
- How citations and freshness are presented.
- How deletion and re-indexing work.
- How retrieval quality is evaluated separately from generation quality.

## Realtime voice

- [OpenAI Realtime and audio](https://developers.openai.com/api/docs/guides/realtime)
- [Realtime WebRTC](https://developers.openai.com/api/docs/guides/realtime-webrtc)
- [Realtime WebSocket](https://developers.openai.com/api/docs/guides/realtime-websocket)
- [Realtime SIP](https://developers.openai.com/api/docs/guides/realtime-sip)
- [Speech to text](https://developers.openai.com/api/docs/guides/speech-to-text)
- [Text to speech](https://developers.openai.com/api/docs/guides/text-to-speech)

Choose WebRTC for browser and mobile interactive media, WebSocket for controlled server-side streaming, and SIP when connecting telephone infrastructure.

## Evaluation

- [OpenAI evaluation best practices](https://developers.openai.com/api/docs/guides/evaluation-best-practices)
- [OpenAI Evals](https://github.com/openai/evals)
- [Evaluate generative AI applications in Microsoft Foundry](https://learn.microsoft.com/en-us/azure/foundry/how-to/evaluate-generative-ai-app)

Build a representative evaluation set before optimizing prompts. Track task success, factuality, tool correctness, safety, latency, and cost. Test model and prompt changes against the same set before release.

## Production checklist

- Keep model identifiers and prompts configurable and versioned.
- Define timeouts, retries, rate-limit handling, and circuit breakers.
- Stream only when it improves user experience.
- Validate structured output before using it in business operations.
- Require human approval for high-impact irreversible actions.
- Minimize sensitive data sent to providers and document retention behavior.
- Add cost budgets, token and request telemetry, caching, and abuse controls.
- Provide graceful degradation when a model or provider is unavailable.
- Record enough trace information to reproduce failures without storing unnecessary private content.
