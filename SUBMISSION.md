# OpenAI submission

Use the [OpenAI submission guide](https://developers.openai.com/plugins/deploy/submission)
and [error reference](https://developers.openai.com/plugins/deploy/submission-errors).

`chatgpt-app-submission.json` contains listing copy, annotation justifications for
21 remote tools, five positive test cases, and three negative test cases. It was
prepared using OpenAI's [submission skill](https://github.com/openai/plugins/blob/main/plugins/openai-developers/skills/chatgpt-app-submission/SKILL.md).
Expected outputs describe acceptance criteria; they are not a record of completed tests.

## Prepare and upload

1. Confirm production `tools/list` advertises the same tool names and annotation
   values as the JSON. Rescan the production MCP server in the portal, then import
   `chatgpt-app-submission.json`. An import cannot fix missing server annotations.
2. Complete the portal's domain verification on the MCP hostname or an allowed
   parent hostname. Keep the account-specific challenge and credentials out of this repository.
3. Use the **With MCP** submission flow for `https://api.greptile.com/mcp` with
   OAuth. Upload the bundled skills and verify both `login` and `review` appear and
   pass scanning. Preserve `scripts/greptile.mjs` and the skills' relative paths.
4. Run all five positive and three negative cases using an isolated reviewer
   account with synthetic repository data. The write cases consume review credits
   or create an inactive rule; use the demo organization. Ensure account access
   and review credits remain available throughout the review period.
5. Verify CLI login and branch review in Codex separately from remote MCP login.
   Record the supported workflows and add the recording URL to the portal.
6. Fill the support URL, directory icons, reviewer credentials and instructions,
   countries, and release notes. Review policy attestations before submitting.

The installable plugin is `plugins/greptile`, not the marketplace repository root.
To create its archive from a committed revision:

```sh
git archive --format=zip --output=/tmp/greptile-plugin.zip HEAD:plugins/greptile
```

This archive includes MCP configuration. Do not use it for the portal's
**Skills only** flow, which excludes MCP configuration. Confirm the portal accepts
the skill upload and includes the bundled CLI before treating packaging as verified.

## Review findings

- No input field explicitly asks for passwords, tokens, MFA codes, payment-card
  data, health information, or government identifiers. Free-form rule text and
  metadata should contain only content the user wants stored in Greptile.
- Tools return account identity, repository content, review comments, and analytics
  within the caller's access. The listing and test instructions describe these uses.
- `trigger_code_review` can consume credits and publish or overwrite review
  feedback on GitHub or GitLab; its annotations must remain non-read-only,
  open-world, and destructive. `create_custom_context` adds private persistent
  data without overwriting an existing record.
- No MCP widget is included, so there is no widget CSP to narrow or UI screenshot
  requirement for this version.
- All 21 tools listed in the JSON currently omit `outputSchema`. Add an
  `outputSchema` so models can use each tool's results more reliably; see the
  [MCP tool specification](https://modelcontextprotocol.io/specification/draft/server/tools#tool).
  This is a recommendation, not a missing-annotation blocker; do not invent schemas
  in the import JSON.
- The OAuth scan reports that enterprise domain restrictions are unavailable.
  Supporting those restrictions requires verified-email OpenID Connect metadata;
  ordinary OAuth tool discovery has succeeded.
