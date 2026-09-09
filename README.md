# Greptile for Codex

The official [Greptile](https://greptile.com) plugin for Codex.

This repository is a Codex plugin marketplace. Add it directly:

```
codex plugin marketplace add greptileai/codex-plugin
codex plugin add greptile@greptile-codex-plugins
```

The plugin gives Codex two ways to work with Greptile:

- the **Greptile MCP server**, for reading and resolving review results and for searching your knowledge base and coding patterns
- the **Greptile CLI**, for reviewing your working branch before a pull request exists

Both authenticate over OAuth against your Greptile account. There is no API key to create and nothing to install — the CLI ships with the plugin, so it needs no npm or Homebrew install, only Node 22+ on your machine.

See [`plugins/greptile`](./plugins/greptile) for setup, workflows, and the full tool list.
