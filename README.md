# A1 Lane — Gemini CLI extension

Draft, schedule and publish social posts from Gemini CLI, with a delivery
receipt for every destination. The extension connects Gemini CLI to your
own A1 Lane workspace through A1 Lane's hosted MCP server — 26 tools for
accounts, media, drafts, approvals, scheduling, batches, receipts and
engagement. Sign-in is OAuth in your browser; there is no API key to paste
and no local server to run.

You need an A1 Lane account (https://a1lane.ai) with at least one connected
social account.

## Install

From the public repository (https://github.com/a1lane/a1lane):

```
gemini extensions install https://github.com/a1lane/a1lane
```

Then restart Gemini CLI, and sign in to A1 Lane:

```
/mcp auth a1lane
```

Your browser opens on A1 Lane's OAuth sign-in; tokens are stored by Gemini
CLI and refreshed automatically. Check the connection any time with `/mcp`
— the `a1lane` server should list its 26 tools.

For local testing:

```
gemini extensions link <path-to-this-folder>
```

## Just the MCP server, without the extension

```
gemini mcp add --transport http a1lane https://a1lane.ai/mcp/v1
```

then `/mcp auth a1lane` inside a session.

## What's inside

- `gemini-extension.json` — the extension manifest: name, description, and
  the `a1lane` MCP server entry (streamable HTTP, OAuth enabled).
- `GEMINI.md` — context Gemini CLI loads with the extension: how the tools
  fit together and the safety rules (approval gate, no automatic resend of
  an uncertain delivery, explicit confirmation before unpublishing,
  read-back honesty).
- `skills/a1-lane/SKILL.md` — the A1 Lane agent skill (full tool guide).
- `icon-1024.png` — the product icon.

## Notes

- The manifest uses `httpUrl` for the streamable-HTTP server. That is the
  field the official Gemini CLI MCP documentation defines for HTTP
  streaming endpoints; `url` is the SSE endpoint field, so `httpUrl` is
  correct for A1 Lane's streamable-HTTP server (verified against the
  official docs 2026-11-09).
- `oauth: { "enabled": true }` turns on Gemini CLI's OAuth handling; with
  discovery, the CLI finds A1 Lane's authorization endpoints from the
  server's metadata on first connection (A1 Lane supports CIMD and Dynamic
  Client Registration). No client id or secret belongs in this file.
