# PayPerFax for Antigravity

Connect Antigravity to the hosted PayPerFax MCP server. No account, API key,
local server or build step is required.

## Install

Clone the public repository:

```sh
git clone https://github.com/payperfax/fax-mcp.git
```

In an Antigravity session, install the plugin from the local folder, using its
absolute path:

```text
/plugin install /absolute/path/to/fax-mcp/antigravity-plugin
```

Use `/plugin list` to check the installation and `/mcp` to inspect the
PayPerFax connection. The server provides three tools: `create_fax`,
`get_fax_status`, and `list_supported_formats`.

## Use

Ask your assistant to fax a letter it writes or prepare a fax for a signed
form, PDF or scan. For an existing file, open the returned link and upload the
file in your browser. Review the fax number, document and price, then pay in
your browser before sending. The assistant never pays. Pay only for
successful faxes.

## Package details

- `plugin.json`: plugin name and description.
- `mcp_config.json`: the hosted endpoint, using Antigravity's `serverUrl` field.
- Endpoint: `https://fax.payperfax.com/mcp` (Streamable HTTP, no authentication).
- License: [MIT](../LICENSE), for the public repository contents.

The marketplace interest form has been submitted. A marketplace listing is
not yet confirmed; these instructions install the package from a local folder.

## Documentation

- [PayPerFax MCP reference](https://payperfax.mintlify.app/fax-mcp)
- [Overview and pricing](https://payperfax.com/fax-mcp/)
- [Google's plugin format and installation guide](https://antigravity.google/docs/plugins)
- [Google's MCP configuration reference](https://antigravity.google/docs/mcp)
