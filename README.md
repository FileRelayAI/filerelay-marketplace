# FileRelay plugin

Use [FileRelay](https://filerelay.ai) to request, receive, list, and share secure file handoffs with other users or agents. This repository packages the shared skill and remote MCP connection for supported agent clients. Install the package for your client, then connect your FileRelay account separately.

## Start in ChatGPT Desktop

Open a Chat or Work conversation and paste:

```text
Read https://github.com/FileRelayAI/filerelay-marketplace. Help me install FileRelay
from the Plugins tab in ChatGPT Desktop and connect my FileRelay account.
If it is not listed, tell me how my workspace admin can import this repository.
After installation, help me create a secure upload link for quarterly reports.
```

Open the Plugins tab, find FileRelay, open its details, and select the plus button to install it. Connect your FileRelay account when prompted. Review the workspace and permissions before approving access.

After installation, start a new Chat or Work conversation. Ask to use FileRelay, or type `@` and select FileRelay.

If FileRelay is not available in your company's Plugins Directory, ask your workspace admin to make it available from this repository. Reading the repository does not activate FileRelay tools. Installation and successful account authentication are required.

See the [ChatGPT Desktop guide](docs/chatgpt-desktop.md) for workspace admin import and account connection details.

## Use FileRelay

- "Create a secure upload link for the financial statements."
- "Show me the completed uploads."
- "Give me a download link for this package that expires in five minutes."
- "Revoke access to this package."

Send the upload link to the person who has the files. After upload, ask for a download link to share. FileRelay provides the links; you choose where to send them.

Files are uploaded through FileRelay's secure page. This plugin does not import attachments from the chat.

## Install in Claude Code

Add the marketplace and install FileRelay:

```text
/plugin marketplace add FileRelayAI/filerelay-marketplace
/plugin install filerelay@filerelay-marketplace
```

Restart Claude Code or run `/reload-plugins`. Use `/mcp` to connect your FileRelay account, then ask Claude to call `who_am_i` and confirm the intended workspace. See the [Claude Code guide](.claude-plugin/README.md).

## Install in Cursor

If FileRelay is available in a Cursor marketplace, open **Customize**, find it, select **Install**, and choose a user or project scope. A team admin can import this repository from **Dashboard > Plugins & MCPs > Team Marketplaces > Add Marketplace > Import from Repo**, then users install it from **Customize**. See the [Cursor guide](.cursor-plugin/README.md).

## Install in Pi

Install the package and use the shared skill:

```sh
pi install git:github.com/FileRelayAI/filerelay-marketplace
pi list
```

Then run `/reload` and `/skill:filerelay`. Configure and authenticate the MCP server separately with `pi mcp add filerelay --url https://www.filerelay.ai/mcp` and `pi mcp login filerelay`. See the [Pi guide](docs/pi.md).

## Skills installer alternative

With Node.js and `npx` installed, add the shared workflow skill with:

```sh
npx skills add FileRelayAI/filerelay-marketplace
```

This installs the skill instructions only. It does not activate or authenticate FileRelay MCP tools. Configure the server in your harness and complete account authentication separately.

## Requirements

A [FileRelay account](https://filerelay.ai) and a client with access to FileRelay MCP tools. Keep credentials in the client's account settings, outside this repository.

## Links

- [FileRelay website](https://filerelay.ai)
- [Report an issue](https://github.com/FileRelayAI/filerelay-marketplace/issues)
- [Changelog](CHANGELOG.md)

## License

[MIT](LICENSE).
