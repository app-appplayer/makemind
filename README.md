# makemind — Let AI Execute Anything

**Control everything with natural language. Every MCP server is an app.**

makemind is the introduction site for the open-source AppPlayer ecosystem — Dart & Flutter packages, the specifications they implement, the runtime cores, and the AppPlayer Standard app. Everything that turns any MCP server into a controllable app.

Live site: [app-appplayer.github.io/makemind](https://app-appplayer.github.io/makemind)

## Published Packages

### Core runtime / orchestration
- [`mcp_bundle`](https://pub.dev/packages/mcp_bundle) — Bundle schema, expression language, standard port catalog (40+), and install pipeline.
- [`mcp_gateway`](https://pub.dev/packages/mcp_gateway) — Multi-node MCP relay with namespace routing, session management, and policy.
- [`mcp_canvas`](https://pub.dev/packages/mcp_canvas) — Universal definition-based canvas for 2D/3D rendering with CDL.
- [`mcp_flow_runtime`](https://pub.dev/packages/mcp_flow_runtime) — Declarative hardware/IoT control flows with platform HAL providers.

### MCP protocol
- [`mcp_client`](https://pub.dev/packages/mcp_client) — Dart MCP client (2025-03-26 spec, OAuth 2.1, JSON-RPC batch).
- [`mcp_server`](https://pub.dev/packages/mcp_server) — Dart MCP server.
- [`mcp_llm`](https://pub.dev/packages/mcp_llm) — LLM provider integration (Claude, OpenAI, Gemini, Bedrock, Cohere, Mistral, Groq, Together, Vertex AI) with Vision / ASR / OCR / Storage adapters.
- [`flutter_mcp`](https://pub.dev/packages/flutter_mcp) — Flutter plugin integrating server / client / LLM with background services.

### Knowledge stack
- [`mcp_knowledge`](https://pub.dev/packages/mcp_knowledge) — Orchestration facade.
- [`mcp_fact_graph`](https://pub.dev/packages/mcp_fact_graph) — Temporal knowledge graph (4-layer L0–L3).
- [`mcp_skill`](https://pub.dev/packages/mcp_skill) — Skill definitions and runtime.
- [`mcp_profile`](https://pub.dev/packages/mcp_profile) — AI persona definitions with appraisal / decision / expression engines.
- [`mcp_knowledge_ops`](https://pub.dev/packages/mcp_knowledge_ops) — Pipelines, workflows, scheduler, runbooks.
- [`mcp_philosophy`](https://pub.dev/packages/mcp_philosophy) — Ethos layer with prohibition checks and pipeline intervention.

### Specialized
- [`mcp_channel`](https://pub.dev/packages/mcp_channel) — Unified messaging connector (Slack, Discord, Email, Kakao, …).
- [`mcp_form`](https://pub.dev/packages/mcp_form) — Form document creation, validation, rendering.
- [`mcp_analysis`](https://pub.dev/packages/mcp_analysis) — Analysis pipeline engine.
- [`mcp_ingest`](https://pub.dev/packages/mcp_ingest) — Document ingestion with chunking, OCR, ASR.
- [`mcp_browser`](https://pub.dev/packages/mcp_browser) — Universal Web Automation Backbone (CDP-direct).

### IO adapters
- [`mcp_io`](https://pub.dev/packages/mcp_io) — Universal I/O Backbone with device registry, policy engine, audit trail.
- [`mcp_io_websocket`](https://pub.dev/packages/mcp_io_websocket), [`mcp_io_http`](https://pub.dev/packages/mcp_io_http), [`mcp_io_mqtt`](https://pub.dev/packages/mcp_io_mqtt), [`mcp_io_serial`](https://pub.dev/packages/mcp_io_serial), [`mcp_io_can`](https://pub.dev/packages/mcp_io_can), [`mcp_io_modbus`](https://pub.dev/packages/mcp_io_modbus), [`mcp_io_opcua`](https://pub.dev/packages/mcp_io_opcua), [`mcp_io_scpi`](https://pub.dev/packages/mcp_io_scpi)

### UI
- [`flutter_mcp_ui_core`](https://pub.dev/packages/flutter_mcp_ui_core) — Core models, constants, M3 14-domain theme, DTCG codec.
- [`flutter_mcp_ui_runtime`](https://pub.dev/packages/flutter_mcp_ui_runtime) — Dynamic UI runtime with M3 theming, responsive form factors, MCP integration.
- [`flutter_mcp_ui_generator`](https://pub.dev/packages/flutter_mcp_ui_generator) — Fluent JSON generation toolkit.

## Specifications

Specs are documents, not code — the formats and contracts the runtime implements. Published at [github.com/app-appplayer/specs](https://github.com/app-appplayer/specs) (MIT).

- `ui_dsl` — Server-driven UI: a JSON DSL the client renders into an interface.
- `bundle` — App packaging: a manifest plus sections that define a bundle.
- `serving` — Bundle MCP serving: run a bundle like a local app.
- `platform` — Composition contract: how UI, bundle, and kernel fit together.

## OS · Core

Runtime kernels the apps run on. Each ships on pub.dev.

- [`appplayer_core`](https://pub.dev/packages/appplayer_core) — AppPlayer runtime core: connection lifecycle, app/dashboard sessions, bundle install, tool dispatch.
- [`flowbrain`](https://pub.dev/packages/flowbrain) — FlowBrain runtime core: declarative flow orchestration kernel.
- [`brain_kernel`](https://pub.dev/packages/brain_kernel) — Knowledge and agent runtime kernel.

## Standard App

- **AppPlayer Standard** — [github.com/app-appplayer/appplayer](https://github.com/app-appplayer/appplayer) — the installable reference app on the stack; one Flutter codebase across Android, iOS, Linux, macOS, Web, Windows.

## How It Works

1. **Run an MCP Server** — server provides UI + Tools + Resources.
2. **AppPlayer connects** as an MCP client.
3. **Dynamic UI renders** the server's UI definition in real-time.
4. **Tools execute** in response to UI actions, controlling devices and services.

## Links

- GitHub organization: [github.com/app-appplayer](https://github.com/app-appplayer)
- pub.dev publisher: [pub.dev/publishers/app-appplayer.com/packages](https://pub.dev/publishers/app-appplayer.com/packages)

---

© 2025 AppPlayer. Open source.
