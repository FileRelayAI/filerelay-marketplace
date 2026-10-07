# FileRelay for Claude Code

## Install

In Claude Code, add the marketplace and install the plugin:

```text
/plugin marketplace add FileRelayAI/filerelay-marketplace
/plugin install filerelay@filerelay-marketplace
```

Restart Claude Code or run `/reload-plugins` after installation.

## Connect FileRelay

Run `/mcp`, choose `filerelay`, and complete the account connection. Ask Claude to call `who_am_i` and confirm that it names the intended workspace. FileRelay is ready only after this authenticated check succeeds.

The plugin provides the shared FileRelay skill and the remote MCP connection. Account authentication is separate from plugin installation. Keep credentials in Claude Code's account settings, never in this repository.

FileRelay uses upload and download links for handoffs. It does not import chat attachments directly. See the [Claude Code plugin documentation](https://code.claude.com/docs/en/plugins) and [marketplace documentation](https://code.claude.com/docs/en/plugin-marketplaces).
