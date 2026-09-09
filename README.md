# Greptile for Codex

The official [Greptile](https://greptile.com) plugin for Codex.

This repository is a Codex plugin marketplace. Add it directly:

```sh
codex plugin marketplace add greptileai/greptile-codex-plugin
codex plugin add greptile@greptile-codex-plugins
```

The plugin gives Codex two ways to work with Greptile:

- the **Greptile MCP server**, for reading review results and searching your
  knowledge base and coding patterns
- the **Greptile CLI**, for reviewing your working branch before a pull request exists

Both authenticate over OAuth against your Greptile account, with separate
sign-ins for MCP and CLI. There is no API key to create and no separate CLI
installation: the CLI ships with the plugin and requires Node 22+.

See [`plugins/greptile`](./plugins/greptile) for setup, workflows, and the full tool list.

## Maintenance

Edit this repository directly. The plugin is no longer generated from another
repository. Keep the marketplace name `greptile-codex-plugins` and plugin name
`greptile` stable for existing installations.

To update the CLI, copy `dist/greptile.js` from the published `greptile` npm
package to `plugins/greptile/scripts/greptile.mjs`, update `greptile.version`,
and bump the plugin version in `plugins/greptile/.codex-plugin/plugin.json`.
Open a PR and run CLI Check and MCP Check. Do not rebuild the npm artifact locally.
