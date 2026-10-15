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

The plugin is packaged for OpenAI with the portable [Agent Plugins](https://developers.openai.com/plugins/build/plugins) layout: `plugin.json` at the plugin root, with the ChatGPT listing copy under `extensions["com.openai"]`. Keep that copy in line with the [plugin guidelines](https://developers.openai.com/plugins/plugin-guidelines): no superlatives, comparisons, testimonials or pricing. The MCP server connection is set up in the OpenAI dashboard, not in the package.

To build the archive for **Plugins → + → Upload plugin** in ChatGPT, zip the plugin folder so it is the archive's only top-level folder:

```bash
cd plugins && rm -f streamline-icons.zip && zip -qr streamline-icons.zip streamline-icons -x '*.DS_Store'
```

The `rm` matters: `zip` adds to an existing archive, so without it files you deleted from the plugin stay in the zip.

The OpenAI dashboard rejects the upload unless:

- `name` in `plugin.json` is the existing plugin's ID (`app-6a5a218d074081919ce8fa4e3fb1e48c`), not `streamline-icons`.
- `shortDescription` (the subtitle) is 30 characters or fewer.
- `version` in `plugin.json` differs from the published one. Bump it for every upload.
- `supportURL` and `logo` are set.
- The plugin has no root `mcp.json`. The dashboard keeps the existing MCP connection and rejects a package that declares one.

Skills are copied into the archive at upload, so re-zip and re-upload after changing them.

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
        ├── .mcp.json                   # Streamline MCP server (Claude)
        ├── assets/icon.png             # ChatGPT composer icon
        ├── assets/logo.png             # Cursor and ChatGPT listing logo
        ├── README.md
        ├── LICENSE
        └── skills/
            └── streamline-expert/
```

## License

Apache License 2.0. See [LICENSE](LICENSE). Assets downloaded through the plugins are licensed under your Streamline plan.
