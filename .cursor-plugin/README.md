# FileRelay for Cursor

## Install from a team marketplace

A Cursor team admin can import this repository:

Team marketplace imports require a Cursor Teams or Enterprise workspace and administrator access.

1. Open **Dashboard > Plugins & MCPs**.
2. In **Team Marketplaces**, select **Add Marketplace**.
3. Select **Import from Repo** and enter `https://github.com/FileRelayAI/filerelay-marketplace`.
4. Review the repository and add the FileRelay plugin to the team marketplace.

The user then opens **Customize**, finds FileRelay, selects **Install**, and chooses a user or project scope.

## Install from a local clone

For a local checkout, clone the repository into Cursor's local plugin directory:

```sh
git clone https://github.com/FileRelayAI/filerelay-marketplace.git ~/.cursor/plugins/local/filerelay
```

Run **Developer: Reload Window**, then install or enable FileRelay from **Customize**. Local plugin loading can be restricted by administrator policy. The local directory must contain the checkout; do not replace it with an external symlink.

The repository's root `plugin.json`, `skills/`, and `mcp.json` are shared with other Agent Plugin clients. Installing the skill does not authenticate or activate the MCP server.

## Connect FileRelay

After installation, open Cursor's MCP settings and select the FileRelay server. Sign in if prompted. Ask the agent to call `who_am_i` and confirm that it names the intended workspace. FileRelay is ready only after this authenticated check succeeds. Keep credentials in Cursor's account settings, never in this repository.

Use Cursor's [plugin documentation](https://cursor.com/docs/plugins) and [plugin reference](https://cursor.com/docs/reference/plugins) for current client behavior.
