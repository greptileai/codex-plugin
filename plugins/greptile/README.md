# Greptile Codex Plugin

Use Greptile from Codex to inspect PRs, address review feedback, and improve repo-specific coding standards.

## Install

```bash
codex plugin marketplace add greptileai/greptile-codex-plugin
codex plugin add greptile@greptile-codex-plugins
```

Set `GREPTILE_API_KEY` in the shell that launches Codex, or sign in through OAuth using Greptile's pre-registered `codex` client. Then start a new task.

## Included skills

- `check-pr`: inspect a GitHub PR, GitLab MR, or Perforce CL for unresolved comments, failing checks, incomplete descriptions, and actionable review feedback.
- `cli-review`: run a Greptile CLI review from the current local checkout and summarize findings.
- `greploop`: iterate until Greptile reaches 5/5 confidence with zero unresolved comments.

## MCP

This plugin bundles Greptile MCP configuration for reading Greptile product data such as PR comments, review state, feedback search, custom context, and review analytics. It uses `GREPTILE_API_KEY` when set and OAuth otherwise.

## Build provenance

- Skills source: https://github.com/greptileai/skills.git
- Branch: main
- Commit: 646e2dfad81e5157e97daecc802b68d3d2c4d1e4
