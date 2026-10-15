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

The first time you use a Streamline tool, sign in with your Streamline account when prompted.

## Install in Cursor

Install **Streamline Icons** from the [Cursor Marketplace](https://cursor.com/marketplace), then sign in with your Streamline account when Cursor connects to the Streamline MCP server.

## ChatGPT and Codex

The plugin is packaged for OpenAI with the portable [Agent Plugins](https://developers.openai.com/plugins/build/plugins) layout: `plugin.json` and `mcp.json` at the plugin root, with the ChatGPT listing copy under `extensions["com.openai"]` in `plugin.json`. Keep that copy in line with the [plugin guidelines](https://developers.openai.com/plugins/plugin-guidelines): no superlatives, comparisons, testimonials or pricing.

To build the archive for **Plugins → + → Upload plugin** in ChatGPT, zip the plugin folder so it is the archive's only top-level folder:

```bash
cd plugins && zip -qr streamline-icons.zip streamline-icons -x '*.DS_Store'
```

To test against a local MCP server, point `url` in `plugins/streamline-icons/mcp.json` at your tunnel before zipping, and don't commit that change. Skills are copied into the archive at upload, so re-zip and re-upload after changing them.

## Repository structure

```text
agent-plugins/
├── .claude-plugin/marketplace.json     # Claude marketplace catalog
├── .cursor-plugin/marketplace.json     # Cursor marketplace catalog
└── plugins/
    └── streamline-icons/
        ├── .claude-plugin/plugin.json  # Claude plugin manifest
        ├── .cursor-plugin/plugin.json  # Cursor plugin manifest
        ├── .cursor-plugin/mcp.json     # Streamline MCP server (Cursor)
        ├── plugin.json                 # OpenAI (ChatGPT and Codex) plugin manifest
        ├── mcp.json                    # Streamline MCP server (OpenAI)
        ├── .mcp.json                   # Streamline MCP server (Claude)
        ├── assets/icon.png             # ChatGPT composer icon
        ├── assets/logo.png             # Cursor marketplace logo
        ├── README.md
        ├── LICENSE
        └── skills/
            └── streamline-expert/
```

## License

Apache License 2.0. See [LICENSE](LICENSE). Assets downloaded through the plugins are licensed under your Streamline plan.
