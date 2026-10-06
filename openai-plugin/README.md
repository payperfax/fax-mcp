# ChatGPT directory package

The package for the ChatGPT plugin directory. It connects only the status endpoint, `https://fax.payperfax.com/mcp/status`, which has one tool, `get_fax_status`. The ChatGPT rules allow commerce only for physical goods and do not allow a link to a checkout page, so the full server at `/mcp` cannot be listed there (payperfax/core#759).

## Files

- `plugin.json`: package identity, listing text, review test cases, publication notes.
- `mcp.json`: the one MCP server.
- `assets/logo.png`: 512 x 512, from the browser extension.

## Before you submit

- [ ] The status endpoint is live on production and returns real status (it is a placeholder on dev now).
- [ ] The three test IDs answer on production (payperfax/core#759, review fixtures).
- [ ] Record the video walkthrough and set `demo_recording_url`.
- [ ] Check that the tracking link in the fourth positive case has the production host.

## Build the ZIP

```
cd openai-plugin && zip -r ../payperfax-openai-plugin.zip plugin.json mcp.json assets
```

## Submit

1. Platform > Plugins > "Upload new or existing plugin". Choose the verified PayPerFax identity.
2. Fix the metadata findings and upload again.
3. MCPs > Connect. Serve the challenge token as plain text at `https://fax.payperfax.com/.well-known/openai-apps-challenge`. Wait for the tool scan.
4. Submit for review. In the reviewer notes:
   > PayPerFax's browser extension already uses its fax-status API to track delivery. This integration brings that same tracking capability into ChatGPT, allowing users to check an existing fax by its tracking ID.
   >
   > Test IDs with fixed responses (they never expire): `00000000-0000-4000-8000-000000000001` (delivered), `00000000-0000-4000-8000-000000000002` (failed), `00000000-0000-4000-8000-000000000003` (pending).
5. After approval, publish.

To change the MCP URL after you submit, you must contact OpenAI support.
