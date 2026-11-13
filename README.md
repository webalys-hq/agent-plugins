# Streamline Agent Plugins

Plugins that bring [Streamline](https://home.streamlinehq.com) icons, illustrations and design elements to AI agents. Each plugin bundles the Streamline MCP server with skills that teach the agent how to use it well.

## Plugins

| Plugin | Description |
| - | - |
| [`streamline-icons`](plugins/streamline-icons) | Search, recommend and download Streamline icons, illustrations and design elements. Includes the `streamline-expert` skill. |

## Install in Claude Code

```bash
/plugin marketplace add webalys-hq/agent-plugins
/plugin install streamline-icons@streamline-icons
```

If you added this marketplace before, refresh it first:

```bash
/plugin marketplace update streamline-icons
```

The Streamline tools work without an account for searching and free assets. Sign in with your Streamline account when prompted to download premium assets.

## Install in Cursor

Install **Streamline Icons** from the [Cursor Marketplace](https://cursor.com/marketplace). It works without an account; sign in with your Streamline account when Cursor asks, to download premium assets.

## ChatGPT and Codex

The plugin is packaged for OpenAI with the portable [Agent Plugins](https://developers.openai.com/plugins/build/plugins) layout: `plugin.json` at the plugin root, with the ChatGPT listing copy under `extensions["com.openai"]`. Keep that copy in line with the [plugin guidelines](https://developers.openai.com/plugins/plugin-guidelines): no superlatives, comparisons, testimonials or pricing. `mcp.json` at the plugin root declares the Streamline MCP server for OpenAI.

To build the archive for **Plugins → + → Upload plugin** in ChatGPT, zip the plugin folder's contents so `plugin.json`, `mcp.json`, `skills/` and `assets/` sit at the archive root. The upload fails with "Invalid plugin package" when they are inside a top-level folder.

```bash
cd plugins/streamline-icons && rm -f ../streamline-icons.zip && zip -qr ../streamline-icons.zip . -x '*.DS_Store' '.mcp.json' '.claude-plugin/*' '.cursor-plugin/*'
```

The `rm` matters: `zip` adds to an existing archive, so without it files you deleted from the plugin stay in the zip. The Claude and Cursor files are left out because OpenAI reads `.mcp.json` as an MCP connection too.

The OpenAI dashboard rejects the upload unless:

- `name` in `plugin.json` matches the plugin you are updating (`streamline-icons`).
- `shortDescription` (the subtitle) is 30 characters or fewer.
- `version` in `plugin.json` differs from the last uploaded one. Bump it for every update.
- `supportURL` and `logo` are set.
- The root `mcp.json` declares the Streamline MCP server. Removing it from an existing plugin isn't supported.

Skills are copied into the archive at upload, so re-zip and re-upload after changing them.

Only one plugin can connect to the Streamline MCP server, and the server's domain-verification token (`/.well-known/openai-apps-challenge`) comes from the `NX_BACKEND_OPENAI_APPS_CHALLENGE_VERIFICATION_CODE` env var in `streamline-api-nestjs`. A new plugin needs its token set there and the public API redeployed.

## MCP Registry listing

[`mcp-registry/server.json`](mcp-registry/server.json) is the Streamline MCP server's entry in the [official MCP Registry](https://registry.modelcontextprotocol.io), published as `com.streamlinehq/mcp`. It used to live in `webalys-hq/streamline-mcp`.

To publish a change:

1. Bump `version` in `server.json`. The registry rejects a version it already has.
2. Push a tag named `mcp-v<version>`, for example `mcp-v2.0.1`. The [Publish to MCP Registry](.github/workflows/publish-mcp-registry.yml) workflow publishes it.

The workflow signs in to the registry with DNS authentication on `streamlinehq.com`, using the `MCP_DNS_PRIVATE_KEY` repository secret. GitHub sign-in only grants the `io.github.webalys-hq/*` namespace, so it can't publish `com.streamlinehq/mcp`. See [DNS authentication](https://modelcontextprotocol.io/registry/authentication#dns-authentication) to generate a new key.

## Repository structure

```text
agent-plugins/
├── .claude-plugin/marketplace.json     # Claude marketplace catalog
├── .cursor-plugin/marketplace.json     # Cursor marketplace catalog
├── .github/workflows/publish-mcp-registry.yml  # Publishes mcp-registry/server.json
├── mcp-registry/server.json            # Official MCP Registry entry
└── plugins/
    └── streamline-icons/
        ├── .claude-plugin/plugin.json  # Claude plugin manifest
        ├── .cursor-plugin/plugin.json  # Cursor plugin manifest
        ├── .cursor-plugin/mcp.json     # Streamline MCP server (Cursor)
        ├── plugin.json                 # OpenAI (ChatGPT and Codex) plugin manifest
        ├── mcp.json                    # Streamline MCP server (OpenAI)
        ├── .mcp.json                   # Streamline MCP server (Claude)
        ├── assets/icon.png             # ChatGPT composer icon
        ├── assets/logo.png             # Cursor and ChatGPT listing logo
        ├── README.md
        ├── LICENSE
        └── skills/
            └── streamline-expert/
                ├── SKILL.md
                ├── agents/openai.yaml  # ChatGPT/Codex skill chip: name, icon, default prompt
                └── assets/             # Skill icons (PNG only: the Claude directory refuses SVG)
```

## License

Apache License 2.0. See [LICENSE](LICENSE). Assets downloaded through the plugins are licensed under your Streamline plan.
