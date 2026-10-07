---
name: otis-analyze
description: >
  Analyze the codebase, build a profile, and recommend which Otis lenses apply for instrumentation.
  Triggers on: "analyze my codebase", "what lenses apply", "profile this repo", /otis-analyze
---

Call the Otis MCP tool `getOtisWorkflow` with `name: "analyze"`, then follow the instructions it returns. They are the current version of this workflow. Fetch them each time; do not work from an earlier copy.

## If the Otis tools are missing

`getOtisWorkflow` comes from the Otis MCP server. Look for it among that server's tools, including any tools your agent loads on demand, before you decide it is missing.

If it is missing, do not attempt the workflow without it. Tell the user the Otis MCP server is not connected, give them the step for their agent, and ask them to sign in and try again:

- Claude Code: `claude mcp add --transport http otis https://app.runotis.com/mcp`, then `/mcp` to sign in
- Codex: `codex mcp add otis --url https://app.runotis.com/mcp`
- Cursor: open `cursor://anysphere.cursor-deeplink/mcp/install?name=otis&config=eyJ1cmwiOiJodHRwczovL2FwcC5ydW5vdGlzLmNvbS9tY3AifQ==`, or add `{"mcpServers": {"otis": {"url": "https://app.runotis.com/mcp"}}}` to `.cursor/mcp.json`
- VS Code: `code --add-mcp '{"name":"otis","type":"http","url":"https://app.runotis.com/mcp"}'`
- Gemini CLI: `gemini mcp add --transport http otis https://app.runotis.com/mcp`, then `/mcp auth otis` to sign in
- Any other agent: add `https://app.runotis.com/mcp` as a remote MCP server

If the server is already added, it may only need the user to sign in.

More detail: https://www.runotis.com/docs/integrations/mcp-server
