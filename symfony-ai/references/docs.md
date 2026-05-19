# Symfony AI Documentation

Use official [Symfony documentation](https://symfony.com/doc) first. Browse the relevant pages at task time because provider names, model examples, and configuration keys may change.

## Core Pages

- [Symfony AI overview](https://symfony.com/doc/current/ai/index.html): Start here for component boundaries: Platform, Agent, Chat, Store, Mate, AI Bundle, MCP Bundle.
- [Platform component](https://symfony.com/doc/current/ai/components/platform.html): Use for direct provider factories, model capabilities, messages, streaming, multimodal input, embeddings, structured output, and `InMemoryPlatform` testing.
- [Agent component](https://symfony.com/doc/current/ai/components/agent.html): Use for agents, processors, tool calling, structured responses, memory, and workflow behavior.
- [AI Bundle](https://symfony.com/doc/current/ai/bundles/ai-bundle.html): Use for Symfony app configuration: `ai.platform`, `ai.agent`, `ai.vectorizer`, stores, indexers, tools, model options, generic OpenAI-compatible services, and cached platforms.
- [Store component](https://symfony.com/doc/current/ai/components/store.html): Use for vector stores and RAG persistence.
- [Chat component](https://symfony.com/doc/current/ai/components/chat.html): Use for conversation persistence and chat-oriented APIs.

## Verification Checklist

- Confirm the installed Symfony AI packages and versions in `composer.json`.
- Confirm whether this app uses `symfony/ai-bundle`, standalone components, or custom vendor clients.
- Confirm the `config/packages/ai.yaml` file exists.
- Confirm required environment variables are declared in project config or deployment docs.
- Confirm the selected model supports needed capabilities: messages, streaming, structured output, image/audio input, embeddings, or tool calling.
- Confirm tests avoid live provider calls unless explicitly requested.
