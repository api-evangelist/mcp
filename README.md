# Model Context Protocol (mcp)

Model Context Protocol is an open, JSON-RPC 2.0 protocol from Anthropic that standardizes how AI applications (hosts) connect to external systems via servers that expose tools, resources, and prompts. MCP is positioned as "a USB-C port for AI applications" and has become the de-facto integration layer for Claude, ChatGPT, Cursor, Visual Studio Code, and a growing ecosystem of agent runtimes. This topic repo catalogs the canonical specification, the official multi-language SDKs, the reference server collection, community registries (Smithery, Pulse MCP), and major MCP-aware clients, plus the vocabulary, JSON Schema, JSON-LD, and example payloads needed to reason about the protocol.

**URL:** [Visit APIs.json URL](https://github.com/api-evangelist/mcp)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - Model Context Protocol, MCP, AI Agents, Tools, Resources, Prompts, JSON-RPC, Anthropic, Standards, Topic

## Timestamps

- **Created:** 2026-05-22
- **Modified:** 2026-05-22

## Landscape

MCP is structured around three actors:

| Actor  | Role |
|--------|------|
| Host   | The LLM application (Claude Desktop, Cursor, VS Code, ChatGPT) that initiates connections, manages consent, and drives the conversation. |
| Client | A connector inside a host that talks to exactly one server over a single transport. |
| Server | A process that exposes tools, resources, and prompts, and may request sampling, roots, and elicitation from the client. |

Servers offer **tools** (callable functions with JSON Schema 2020-12 input), **resources** (URI-addressable context), and **prompts** (templated workflows). Clients may offer **sampling** (server-initiated LLM calls), **roots** (filesystem boundaries), and **elicitation** (user input requests). All traffic is JSON-RPC 2.0 over **stdio** (local) or **Streamable HTTP** (remote, with optional OAuth 2.1). The current dated specification version is **2025-11-25**.

## Feature Matrix

| Feature | Surface | Initiator | Notification |
|---------|---------|-----------|--------------|
| Tools | `tools/list`, `tools/call` | Client → Server | `notifications/tools/list_changed` |
| Resources | `resources/list`, `resources/read`, `resources/subscribe` | Client → Server | `notifications/resources/list_changed`, `notifications/resources/updated` |
| Prompts | `prompts/list`, `prompts/get` | Client → Server | `notifications/prompts/list_changed` |
| Sampling | `sampling/createMessage` | Server → Client | — |
| Roots | `roots/list` | Server → Client | `notifications/roots/list_changed` |
| Elicitation | `elicitation/create` | Server → Client | — |
| Completion | `completion/complete` | Client → Server | — |
| Logging | `logging/setLevel`, `notifications/message` | Bidirectional | — |
| Progress | `notifications/progress` | Bidirectional | — |
| Cancellation | `notifications/cancelled` | Bidirectional | — |

## APIs

### MCP Specification

The authoritative protocol definition for the Model Context Protocol, maintained at modelcontextprotocol.io and in the modelcontextprotocol/specification GitHub repository. The TypeScript schema (`schema.ts`) is the source of truth, with an auto-generated JSON Schema (`schema.json`) for tooling. The current dated version is **2025-11-25**.

**Human URL:** [https://modelcontextprotocol.io/specification](https://modelcontextprotocol.io/specification)

#### Properties

- [Documentation](https://modelcontextprotocol.io/specification/2025-11-25)
- [GitHubRepository](https://github.com/modelcontextprotocol/specification)
- [JSONSchema](https://github.com/modelcontextprotocol/specification/blob/main/schema/2025-11-25/schema.json)
- [Versioning](https://modelcontextprotocol.io/specification/versioning)

### Official SDKs

| Language | Package | Repo |
|----------|---------|------|
| TypeScript | [`@modelcontextprotocol/sdk`](https://www.npmjs.com/package/@modelcontextprotocol/sdk) | [typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) |
| Python | [`mcp`](https://pypi.org/project/mcp/) | [python-sdk](https://github.com/modelcontextprotocol/python-sdk) |
| Java | Maven Central | [java-sdk](https://github.com/modelcontextprotocol/java-sdk) |
| Kotlin | — | [kotlin-sdk](https://github.com/modelcontextprotocol/kotlin-sdk) |
| C# | NuGet (Microsoft collab) | [csharp-sdk](https://github.com/modelcontextprotocol/csharp-sdk) |
| Swift | SwiftPM | [swift-sdk](https://github.com/modelcontextprotocol/swift-sdk) |
| Rust | crates.io | [rust-sdk](https://github.com/modelcontextprotocol/rust-sdk) |

### Reference Servers and Tooling

- [Reference Servers](https://github.com/modelcontextprotocol/servers) — Everything, Fetch, Filesystem, Git, Memory, Sequential Thinking, Time.
- [MCP Inspector](https://github.com/modelcontextprotocol/inspector) — `npx @modelcontextprotocol/inspector`, web UI at `localhost:6274`.
- [Official Registry](https://github.com/modelcontextprotocol/registry) — Anthropic-maintained server index, API freeze v0.1.

### Third-Party Registries

- [Smithery](https://smithery.ai) — Server registry plus hosted runtime.
- [Pulse MCP](https://www.pulsemcp.com) — Directory and news site; sub-registry API implements the Generic MCP Registry API specification.

### MCP Hosts

- [Claude Desktop / Claude Code / Claude API](https://claude.com/docs/connectors/building)
- [Cursor](https://cursor.com/docs/context/mcp)
- [Visual Studio Code (Copilot Chat)](https://code.visualstudio.com/docs/copilot/chat/mcp-servers)
- [ChatGPT (Apps SDK)](https://developers.openai.com/api/docs/mcp/)

## Common Properties

- [Portal](https://modelcontextprotocol.io)
- [Documentation](https://modelcontextprotocol.io/introduction)
- [GitHubOrganization](https://github.com/modelcontextprotocol)
- [GitHubRepository](https://github.com/modelcontextprotocol/specification)
- [Vocabulary](vocabulary/mcp-vocabulary.yml)
- [JSONLD](json-ld/mcp-context.jsonld)

## Features

| Name | Description |
|------|-------------|
| JSON-RPC 2.0 Base Protocol | MCP defines request, response, and notification message shapes on top of JSON-RPC 2.0 with strict rules on IDs and structure. |
| Stateful Sessions | Clients and servers negotiate capabilities during the initialize handshake and maintain stateful connections for the lifetime of the session. |
| Tools | Servers expose callable tools with JSON Schema 2020-12 input schemas; clients invoke them via `tools/call`. |
| Resources | Servers expose URI-addressable context (files, database rows, API responses) via `resources/list`, `resources/read`, and subscription notifications. |
| Prompts | Servers expose templated prompts and workflows via `prompts/list` and `prompts/get` for users to invoke. |
| Sampling | Clients can offer `sampling/createMessage` so servers can ask the host LLM to run agentic, recursive inference under user consent. |
| Roots | Clients can advertise filesystem roots that bound a server's operating scope via `roots/list`. |
| Elicitation | Servers can request additional information from users mid-session via `elicitation/create`. |
| Multiple Transports | MCP defines stdio for local processes and Streamable HTTP (with an optional SSE legacy mode) for networked deployments. |
| OAuth 2.1 Authorization | HTTP-based transports follow an MCP-defined OAuth 2.1 authorization framework; stdio transports retrieve credentials from the environment. |
| Icons and Branding | Implementations, tools, prompts, and resources can publish icon metadata for richer UIs, with strict security constraints on icon URIs. |
| Reserved `_meta` Namespace | MCP reserves the `_meta` property with a structured prefix/name format for attaching additional metadata to interactions. |

## Use Cases

| Name | Description |
|------|-------------|
| IDE Augmentation | MCP servers extend coding assistants like Cursor, VS Code Copilot, and Claude Code with project-aware tools, repository search, and terminal/build access. |
| Knowledge Base Access | MCP resources surface documentation, wikis, and structured data stores to AI hosts under user consent. |
| Workflow Automation | MCP tools let agents trigger build pipelines, send notifications, create tickets, and orchestrate multi-step business workflows. |
| Enterprise Connectors | Vendors expose enterprise systems (CRMs, ITSM, data warehouses) as MCP servers so that any MCP-aware host can connect without bespoke integration code. |
| Local Computer Use | Local MCP servers expose filesystem, git, shell, browser, and desktop automation tools to assistants running on the same machine. |

## Integrations

| Name | Description |
|------|-------------|
| Anthropic Claude | Claude Desktop, Claude Code, and the Claude API are first-class MCP hosts and the protocol's reference consumers. |
| OpenAI ChatGPT | ChatGPT supports MCP through the Apps SDK and OpenAI's developer docs. |
| Cursor | Cursor IDE consumes MCP servers via `mcp.json` configuration. |
| Visual Studio Code | VS Code's Copilot Chat treats MCP servers as agents and tools. |
| MCPJam | MCPJam is a community client implementation for testing MCP servers interactively. |
| Naftiko Sandbox | Naftiko Sandbox is a governed MCP host that compiles capability definitions into sandboxed MCP servers running in containers with policy enforcement. |

## Solutions

| Name | Description |
|------|-------------|
| Spec, SDKs, and Reference Servers | modelcontextprotocol.io publishes the spec, schema, official SDKs for TypeScript, Python, Java, Kotlin, C#, Swift, and Rust, plus a set of reference servers and an Inspector debugging tool. |
| Official Registry | The official MCP Registry is a central index of MCP servers with GitHub OAuth/OIDC and DNS-based ownership verification. |
| Third-Party Registries | Smithery and Pulse MCP provide alternative discovery surfaces and, in Smithery's case, hosted execution of community servers. |
| Vendor Hosts | Claude, ChatGPT, Cursor, VS Code Copilot, Continue, Cline, Zed, Windsurf, and many other assistants act as MCP hosts. |

## Artifacts

Machine-readable descriptions of the protocol surface.

### JSON Schema

- [MCP JSON-RPC Message](json-schema/mcp-jsonrpc-message-schema.json)
- [MCP Initialize](json-schema/mcp-initialize-schema.json)
- [MCP Tool](json-schema/mcp-tool-schema.json)
- [MCP tools/call](json-schema/mcp-call-tool-schema.json)
- [MCP Resource](json-schema/mcp-resource-schema.json)
- [MCP Prompt](json-schema/mcp-prompt-schema.json)
- [MCP sampling/createMessage](json-schema/mcp-sampling-schema.json)
- [MCP Root](json-schema/mcp-root-schema.json)

### JSON-LD

- [MCP Context](json-ld/mcp-context.jsonld) — aligns MCP types with schema.org where possible (Host/Client/Server as SoftwareApplication/WebAPI, Tool as Action, Resource as DigitalDocument, Prompt as CreativeWork).

### Examples

- [Initialize Request](examples/mcp-initialize-request-example.json)
- [Initialize Result](examples/mcp-initialize-result-example.json)
- [tools/list](examples/mcp-tools-list-example.json)
- [tools/call](examples/mcp-tools-call-example.json)
- [resources/list](examples/mcp-resources-list-example.json)
- [resources/read](examples/mcp-resources-read-example.json)
- [prompts/get](examples/mcp-prompts-get-example.json)
- [sampling/createMessage](examples/mcp-sampling-create-message-example.json)
- [roots/list](examples/mcp-roots-list-example.json)
- [notifications/progress](examples/mcp-progress-notification-example.json)
- [Error response](examples/mcp-error-response-example.json)

## Vocabulary

- [MCP Vocabulary](vocabulary/mcp-vocabulary.yml) — operational dimension (actors, JSON-RPC methods, transports) and capability dimension (features, capabilities, personas, workflows, security), plus the registry surface.

## Notable Absences

- No public OpenAPI: MCP is JSON-RPC, not REST. The authoritative contract is the TypeScript schema at `schema/2025-11-25/schema.ts`.
- No public AsyncAPI: although MCP is bidirectional and event-bearing, the project ships JSON Schema rather than AsyncAPI.
- No commercial plans or rate limits at the protocol level: registries and hosts publish their own quotas; the spec itself imposes none.

## Maintainers

**FN:** Kin Lane

**Email:** kinlane@gmail.com
