# Greptile Codex Plugin

Use Greptile reviews, MCP tools, and agent skills in OpenAI Codex.

## Private test install

You need GitHub access to this repository while it is private.

```bash
codex plugin marketplace add greptileai/greptile-codex-plugin
codex plugin add greptile@greptile-codex-plugins
```

Set your Greptile API key in the shell that launches Codex:

```bash
export GREPTILE_API_KEY="your-api-key"
```

Start a new Codex task after installation.

## Included skills

- `check-pr`: inspect PR readiness and unresolved review feedback.
- `cli-review`: run a Greptile CLI review from a local checkout.
- `greploop`: fix feedback and re-review until the PR is clean.

The plugin also configures the public Greptile MCP endpoint at `https://api.greptile.com/mcp`.

## Verify

```bash
codex plugin marketplace list
codex plugin list
```

The marketplace should appear as `greptile-codex-plugins`, with the `greptile` plugin installed.

## Update

```bash
codex plugin marketplace upgrade greptile-codex-plugins
codex plugin add greptile@greptile-codex-plugins
```

Start a new Codex task after updating.

## Package contents

This repository contains only the distributable marketplace package. Plugin skills are built from
the public [`greptileai/skills`](https://github.com/greptileai/skills) repository.
