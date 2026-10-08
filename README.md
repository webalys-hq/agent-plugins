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

## Repository structure

```text
agent-plugins/
├── .claude-plugin/marketplace.json     # Claude marketplace catalog
├── .cursor-plugin/marketplace.json     # Cursor marketplace catalog
└── plugins/
    └── streamline-icons/
        ├── .claude-plugin/plugin.json  # Claude plugin manifest
        ├── .cursor-plugin/plugin.json  # Cursor plugin manifest
        ├── .mcp.json                   # Streamline MCP server (Claude)
        ├── mcp.json                    # Streamline MCP server (Cursor)
        ├── assets/logo.png             # Cursor marketplace logo
        ├── README.md
        ├── LICENSE
        └── skills/
            └── streamline-expert/
```

## License

Apache License 2.0. See [LICENSE](LICENSE). Assets downloaded through the plugins are licensed under your Streamline plan.
