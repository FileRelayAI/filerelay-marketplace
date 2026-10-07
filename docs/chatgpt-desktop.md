# FileRelay for ChatGPT Desktop

This guide is for an assistant helping a user install FileRelay and connect their account. The user provides the repository URL, approves installation, and signs in to FileRelay.

## Install in ChatGPT Desktop

Read the root `plugin.json`, `mcp.json`, and `skills/filerelay/SKILL.md`. This repository is the plugin package. Its marketplace catalog is at `.agents/plugins/marketplace.json`.

Help the user open the Plugins tab, find FileRelay, open its details, and select the plus button to install it. After installation, start a new Chat or Work conversation. The user can ask to use FileRelay or type `@` and select it.

If FileRelay is not available, a workspace admin can import `https://github.com/FileRelayAI/filerelay-marketplace` under **Admin > Plugins > Add > Import marketplace**, leave **Path** empty, and make FileRelay available to the user. The user then installs it from their workspace's Plugins Directory.

After import, the admin must confirm FileRelay's installation policy for the user's role and when account connection is required. GitHub import does not apply the repository's installation or authentication policies. Each user connects their own FileRelay account.

If the available Desktop controls cannot install this repository, explain the missing installation capability. For the current client installation paths, follow the [README instructions](../README.md#start-in-chatgpt-desktop).

Repository reading alone does not activate FileRelay tools. Confirm that installation succeeded and the tools are available before claiming that the plugin is ready.

## Connect the user's account

Help the user follow the FileRelay account connection prompt. The user signs in on FileRelay, checks the workspace and permissions, and approves access.

Use `who_am_i` to confirm the connected workspace before creating an upload request or issuing a download link. If it names the wrong workspace, stop and help the user reconnect to the intended account.

If account connection fails, report that the FileRelay connection is not ready. Keep user setup limited to installation, sign-in, and approval of workspace access. Do not claim that a connected account exists until an authenticated tool call succeeds.

## Complete the first handoff

1. Ask what files the user wants to receive, then create an upload request.
2. Give the user the secure upload link to share with the sender.
3. After the sender uploads, list the completed packages.
4. Create an expiring download link for the selected package when the user asks.

Follow `skills/filerelay/SKILL.md` for the full workflow and revocation rules.

References: [Plugin packaging](https://developers.openai.com/plugins/build/plugins), [GitHub workspace import](https://learn.chatgpt.com/docs/enterprise/plugin-management), and [Install and use plugins](https://learn.chatgpt.com/docs/plugins?surface=app).
