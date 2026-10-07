# FileRelay for Pi

## Install the package

Install the repository as a Pi package, then confirm it is listed:

```sh
pi install git:github.com/FileRelayAI/filerelay-marketplace
pi list
```

Reload Pi and invoke the shared skill:

```text
/reload
/skill:filerelay
```

Package installation adds the skill. It does not activate or authenticate the FileRelay MCP server.

## Add and authenticate the MCP server

Pi includes MCP support. Add the FileRelay server, sign in, and verify the connection:

```sh
pi mcp add filerelay --url https://www.filerelay.ai/mcp
pi mcp login filerelay
pi mcp list
```

Run `/reload` after changing MCP configuration outside the current session. Pi stores package settings in `~/.pi/agent/settings.json` and MCP settings in `~/.pi/agent/mcp.json`.

Ask Pi to call `who_am_i` and confirm that it names the intended workspace. FileRelay is ready only after this authenticated check succeeds. FileRelay uses upload and download links for handoffs and does not import chat attachments directly.

See Pi's [package documentation](https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/packages.md) and [MCP documentation](https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/mcp.md).
