# PayPerFax MCP server

[![PayPerFax MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/com.payperfax/fax/badges/score.svg)](https://glama.ai/mcp/connectors/com.payperfax/fax)
[![PayPerFax on Smithery](https://img.shields.io/badge/Smithery-PayPerFax-orange)](https://smithery.ai/servers/adam-cr0c/payperfax)
[![Listed on mcpservers.org](https://mcpservers.org/badge.svg)](https://mcpservers.org/servers/payperfax/fax-mcp)

Send a fax from your AI assistant. Pay per fax. No account, no API key, no subscription.

The assistant prepares the fax. You open the link, see the preview with the price, and pay in the browser. Nothing is sent and nothing is charged before you pay. A fax that fails to transmit is not charged.

```
https://fax.payperfax.com/mcp
```

Remote server, Streamable HTTP, no authentication.

## Add it to your chat app

1. Open the connector settings ("Connectors", "Integrations" or "MCP servers").
2. Add a custom MCP server. Name: `PayPerFax`. URL: `https://fax.payperfax.com/mcp`.
3. Turn the connector on in your chat.

Tell the assistant which country you are in, so the price shows in your currency. The preview, the payment page and the emails can be in English, Spanish, German, French, Japanese or Korean.

## Add it to Gemini CLI

Install the extension from this repository:

```sh
gemini extensions install https://github.com/payperfax/fax-mcp --ref main
```

The extension connects to the hosted PayPerFax MCP server. No account or API key is required.
In Gemini CLI, use `/mcp` to check the connection and see the three tools.

## Add it to Antigravity

The [Antigravity plugin package](antigravity-plugin/) connects to the hosted
PayPerFax MCP server. See its [installation instructions](antigravity-plugin/README.md)
to install it from a local folder. Marketplace listing is pending.

## Tools

| Tool                     | What it does                                                                                                                                         |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `create_fax`             | Prepares a fax and returns a link. The assistant gives the fax number, your email address, and either a letter it wrote (Markdown) or a notice that a file is still needed |
| `get_fax_status`         | Reads the status of a fax: queued, sending, delivered or failed                                                                                      |
| `list_supported_formats` | Lists the input types, the size limits and the languages                                                                                             |

The assistant never pays. A person pays, in the browser, every time.

## Files

MCP does not carry files from a chat app to a server. So:

- **The assistant writes the document.** The letter goes as Markdown text and becomes the fax.
- **You have the file** (a signed form, a scan, a PDF). The link opens a pre-filled form. You add the file in the browser.

A coding agent with a shell (Claude Code, Codex, Cursor) can also send a file over HTTP. See the [PayPerFax API](https://payperfax.com/pay-per-fax-api/).

## Example: fax a form to the IRS

> Fax my signed Form 2848 to the IRS. I'm in the US.

The assistant takes the fax number from irs.gov and shows you the source. It calls `create_fax` with a notice that a file is expected. You open the link, add the signed PDF, check the number on the preview, and pay.

Always check the number against irs.gov. A wrong number sends tax papers to a stranger. Guide: [Fax a form to the IRS with an AI agent](https://payperfax.mintlify.app/guides/fax-the-irs).

## Documentation

- [Fax MCP](https://payperfax.com/fax-mcp/): overview, price, FAQ
- [MCP server reference](https://payperfax.mintlify.app/fax-mcp): tools, fields, rate rules
- [Guide for AI assistants](https://payperfax.mintlify.app/agents)
- [Pricing](https://payperfax.com/price/)
- [Security](https://payperfax.com/policy/security/)

## About this repository

This repository documents the hosted server. The server code is not open source. [`server.json`](server.json) is the entry in the [official MCP registry](https://registry.modelcontextprotocol.io/) as `com.payperfax/fax`.

The files in this public repository are available under the [MIT License](LICENSE).
That license does not cover the hosted server implementation, which is not included here.
