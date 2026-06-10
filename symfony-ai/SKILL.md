---
name: symfony-ai
description: Use when working with Symfony AI documentation or implementing integrations with LLM providers such as OpenAI, Anthropic, or Google Gemini embeddings, structured output, tool calling, streaming, multimodal input, or AI Bundle platform/agent configuration.
---

# Symfony AI

## Workflow

Use this skill for Symfony AI provider work. Treat Symfony AI as fast-moving: verify current official docs before changing code or giving definitive configuration advice.

1. Read `references/docs.md` to pick the relevant official Symfony AI docs.
2. Browse the selected official docs pages before implementing provider-specific behavior.
3. Inspect the local project for existing Symfony AI, Gemini, LLM, HTTP client, env var, and service configuration patterns.
4. Prefer Symfony AI Bundle configuration in `config/packages/ai.yaml` for Symfony apps. Use the standalone Platform component only when the project already uses it directly or the task explicitly asks for component-level code.
5. Keep provider secrets in the [Symfony Secrets component](https://symfony.com/doc/current/configuration/secrets.html). **DO NOT** hard-code API keys, model names tied to private deployments, tenant IDs, or endpoints.
6. Add tests with fake/in-memory platforms or mocked clients where practical. Avoid tests that call live LLM APIs unless the user explicitly asks for integration testing.

## Implementation Notes

- Use `ai.platform.<provider>` service IDs from the AI Bundle when wiring agents, vectorizers, or stores.
- For Google Gemini, start from `ai.platform.gemini` configuration and `GEMINI_API_KEY` unless existing project conventions say otherwise.
- For tool calling, read the Agent and AI Bundle tool sections; register application tools with `#[AsTool]` and restrict injected tools per agent when broad access is not intended.
- For structured extraction, prefer Symfony AI structured output support when the provider/model supports it, and still validate returned data in application code. Additionally, use PHP DTO classes to define structured output schemas:
  - https://symfony.com/doc/current/ai/components/platform.html#php-classes-as-output
  - https://raw.githubusercontent.com/symfony/ai/refs/heads/main/examples/openai/structured-output-math.php
- For RAG or embeddings, read Platform embeddings, Store, Vectorizer, and Indexer docs together; the provider config alone is not enough.

## Project Fit

In this repository, respect the RICH module pattern and existing Symfony conventions. Place business behavior in module handlers/services instead of controllers, use immutable DTOs where data crosses boundaries, and run the project’s normal validation command when code changes are made.
