# Model Context Protocol (MCP)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Model Context Protocol is an open, JSON-RPC 2.0 protocol from Anthropic that standardizes how AI applications (hosts) connect to external systems via servers that expose tools, resources, and prompts. MCP is positioned as "a USB-C port for AI applications" and has become the de-facto integration layer for Claude, ChatGPT, Cursor, Visual Studio Code, and a growing ecosystem of agent runtimes. This topic repo catalogs the canonical specification, the official multi-language SDKs, the reference server collection, community registries (Smithery, Pulse MCP, Naftiko Sandbox), and major MCP-aware clients, plus the vocabulary, JSON Schema, JSON-LD, and example payloads needed to reason about the protocol.

**Areas:** MCP · AI Agents · Tools · Resources · Prompts · JSON-RPC · Anthropic · Standards · Topic · A2A

## Model Context Protocol (MCP) on APIs.io

Everything profiled for Model Context Protocol (MCP) is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/mcp/](https://apis.io/providers/mcp/)** — or go straight to one of the APIs or properties below.

### APIs (17)

- [MCP Specification](https://apis.io/apis/mcp/mcp-specification/) — The authoritative protocol definition for the Model Context Protocol, maintained at modelcontextprotocol.io and in the modelcontextprotocol/ specification…
- [MCP TypeScript SDK](https://apis.io/apis/mcp/mcp-typescript-sdk/) — Official TypeScript SDK published as @modelcontextprotocol/sdk on npm. Dual-purpose library for building MCP servers and clients on Node.js, Bun, and Deno.…
- [MCP Python SDK](https://apis.io/apis/mcp/mcp-python-sdk/) — Official Python SDK published as `mcp` on PyPI. Includes the FastMCP high-level framework with decorators for tools, resources, and prompts; low-level…
- [MCP Java SDK](https://apis.io/apis/mcp/mcp-java-sdk/) — Official Java SDK for building MCP servers and clients on the JVM. Maintained in the modelcontextprotocol/java-sdk repository.
- [MCP Kotlin SDK](https://apis.io/apis/mcp/mcp-kotlin-sdk/) — Official Kotlin SDK for MCP servers and clients targeting Kotlin and Android runtimes.
- [MCP C# SDK](https://apis.io/apis/mcp/mcp-c-sdk/) — Official C# SDK for .NET, maintained in collaboration with Microsoft.
- [MCP Swift SDK](https://apis.io/apis/mcp/mcp-swift-sdk/) — Official Swift SDK for MCP servers and clients on Apple platforms.
- [MCP Rust SDK](https://apis.io/apis/mcp/mcp-rust-sdk/) — Official Rust SDK for MCP servers and clients.
- [MCP Reference Servers](https://apis.io/apis/mcp/mcp-reference-servers/) — Canonical collection of reference MCP server implementations maintained by the project. The active servers (Everything, Fetch, Filesystem, Git, Memory,…
- [MCP Inspector](https://apis.io/apis/mcp/mcp-inspector/) — Developer tool for testing and debugging MCP servers. React-based web UI plus Node.js proxy, launched with `npx @modelcontextprotocol/inspector` and…
- [Official MCP Registry](https://apis.io/apis/mcp/official-mcp-registry/) — Community-driven, Anthropic-maintained registry that functions as an app store for MCP servers. Allows developers to publish server definitions and clients…
- [Smithery](https://apis.io/apis/mcp/smithery/) — Third-party MCP server registry and hosted runtime. Catalogs community-built MCP servers, generates installation snippets for clients like Claude Desktop…
- [Pulse MCP](https://apis.io/apis/mcp/pulse-mcp/) — Third-party MCP directory and news site. Maintains a sub-registry API that implements the Generic MCP Registry API specification with PulseMCP-specific…
- [Claude Desktop (MCP Host)](https://apis.io/apis/mcp/claude-desktop-mcp-host/) — Anthropic's Claude Desktop application was the first MCP host. Connects to local MCP servers via stdio transport defined in claude_desktop_config .json and…
- [Cursor (MCP Host)](https://apis.io/apis/mcp/cursor-mcp-host/) — Cursor IDE supports MCP servers as a first-class extension mechanism, configured via mcp.json. Cursor is one of the most widely used MCP hosts for…
- [Visual Studio Code (MCP Host)](https://apis.io/apis/mcp/visual-studio-code-mcp-host/) — VS Code's GitHub Copilot Chat integrates MCP servers as agents and tools. Microsoft has standardized on MCP for Copilot's agent-mode extensibility.
- [ChatGPT (MCP Host)](https://apis.io/apis/mcp/chatgpt-mcp-host/) — OpenAI's ChatGPT supports MCP through the Apps SDK and developer tooling documented at developers.openai.com, making MCP a cross-vendor surface for…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### JSON Schema (8)

The data models the API reads and writes.

- [MCP tools/call Request and Result](https://apis.io/schemas/mcp/mcp-call-tool/)
- [MCP Initialize Request and Result](https://apis.io/schemas/mcp/mcp-initialize/)
- [MCP JSON-RPC Message](https://apis.io/schemas/mcp/mcp-jsonrpc-message/)
- [MCP Prompt](https://apis.io/schemas/mcp/mcp-prompt/)
- [MCP Resource](https://apis.io/schemas/mcp/mcp-resource/)
- [MCP Root](https://apis.io/schemas/mcp/mcp-root/)
- [MCP sampling/createMessage Request and Result](https://apis.io/schemas/mcp/mcp-sampling/)
- [MCP Tool](https://apis.io/schemas/mcp/mcp-tool/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Mcp Context](https://apis.io/jsonld/mcp/mcp-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Model Context Protocol Vocabulary](https://apis.io/vocabularies/mcp/mcp-vocabulary/)

#### Examples (11)

Example requests and responses.

- [Mcp Error Response Example](https://apis.io/examples/mcp/mcp-error-response-example/)
- [Mcp Initialize Request Example](https://apis.io/examples/mcp/mcp-initialize-request-example/)
- [Mcp Initialize Result Example](https://apis.io/examples/mcp/mcp-initialize-result-example/)
- [Mcp Progress Notification Example](https://apis.io/examples/mcp/mcp-progress-notification-example/)
- [Mcp Prompts Get Example](https://apis.io/examples/mcp/mcp-prompts-get-example/)
- [Mcp Resources List Example](https://apis.io/examples/mcp/mcp-resources-list-example/)
- [Mcp Resources Read Example](https://apis.io/examples/mcp/mcp-resources-read-example/)
- [Mcp Roots List Example](https://apis.io/examples/mcp/mcp-roots-list-example/)
- [Mcp Sampling Create Message Example](https://apis.io/examples/mcp/mcp-sampling-create-message-example/)
- [Mcp Tools Call Example](https://apis.io/examples/mcp/mcp-tools-call-example/)
- [Mcp Tools List Example](https://apis.io/examples/mcp/mcp-tools-list-example/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Model Context Protocol (MCP) — jsonschema rules](https://apis.io/rules/mcp/mcp-jsonschema-spectral-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Mcp Domain Security](https://apis.io/security/mcp/mcp-domain-security/)
- [Mcp Vulnerability Disclosure](https://apis.io/security/mcp/mcp-vulnerability-disclosure/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://modelcontextprotocol.io/)
- [Documentation](https://modelcontextprotocol.io/introduction)
- [Blog](https://blog.modelcontextprotocol.io/index.xml)
- [GitHub](https://github.com/modelcontextprotocol)

## API Evangelist rating

**Kin Score 26.8** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 58.9 |
| Contract quality | 21.9 |
| Contract governance | 23.5 |
| Operational transparency | 28.9 |
| Developer ergonomics | 42.9 |
| Access clarity | 0.0 |

**Agent readiness 3.5** — human-only

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | — |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | — |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | near-conformant (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 16.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/mcp/](https://apis.io/providers/mcp/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Model Context Protocol (MCP): the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/mcp/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
