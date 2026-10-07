---
name: filerelay
description: Use FileRelay to request, receive, list, and share secure file handoffs with other users or agents.
---

# FileRelay file handoffs

Use the FileRelay MCP tools for short-lived file handoffs. Call `who_am_i` before a mutation and check that it names the intended workspace. Ask the user only when the workspace is wrong or unclear.

## Receive files and share them

1. Call `create_upload_request` with the required file count and expiry.
2. Give the returned secure upload URL to the sender. The sender opens that page and uploads the files directly to FileRelay storage.
3. Wait until the upload is complete, then call `list_received_packages`.
4. Call `issue_download_link` only for a completed package. Use the default five-minute link lifetime unless the user asks for another value within the package retention limit.
5. Return the expiring FileRelay link. FileRelay does not send email or forward the link. Ask before sending the link through another channel.

Do not claim that ChatGPT imported an attachment or generated a file. FileRelay's MCP tools accept file metadata and return direct upload instructions. They do not proxy file bytes through the MCP server.

## Send files supplied outside the MCP call

For a file that is already available to a client with an uploader, call `create_package` with file metadata, upload the bytes directly to the returned R2 slot URLs, collect the object-store ETags, and call `finalize_package`. Call `issue_download_link` only after finalization reports an available package. If the file is not available to such a client, use `create_upload_request` and have the sender upload through the secure page.

## Inspect and revoke

Use `list_received_packages` to find completed, expired, or revoked packages in the current workspace. Use `revoke_package` when the user asks to stop access. Revocation blocks new FileRelay grants and existing FileRelay links immediately. An already-issued direct R2 download URL can remain valid until its short expiry, five minutes by default and at most one hour. Deleted objects are unavailable, and provider deletion failures may delay cleanup. A direct upload URL is signed for 15 minutes. A downloaded copy cannot be recalled.

Report these conditions as returned by the tool: wrong workspace, expired or revoked package, failed upload or finalization, inactive billing access, and missing permissions. `Idempotency-Key` is an HTTP header, not a tool argument. If the client can set that header, reuse the same key for the same operation. Never retry a mutation with a new key after an uncertain response. If the client cannot set the header, inspect existing state or report uncertainty instead of retrying blindly.
