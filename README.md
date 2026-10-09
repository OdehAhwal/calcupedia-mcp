<p align="center">
  <img src="assets/icon.png" width="96" height="96" alt="Calcupedia logo">
</p>

<h1 align="center">Calcupedia MCP server</h1>

<p align="center">
  2,400+ calculators and unit converters for Claude and other AI assistants, with a live calculator card in the chat.
</p>

<p align="center">
  <a href="https://calcupedia.io/mcp">Docs</a> ·
  <a href="https://registry.modelcontextprotocol.io/v0.1/servers?search=io.calcupedia/calcupedia">MCP Registry</a> ·
  <a href="https://smithery.ai/servers/calcupedia/calcupedia">Smithery</a> ·
  <a href="https://calcupedia.io">calcupedia.io</a>
</p>

---

Calcupedia is a hosted, remote MCP server. You don't install or run anything: point your MCP client at the URL below.

```
https://calcupedia.io/api/mcp
```

- **Transport:** Streamable HTTP
- **Auth:** none (no account, no API key)
- **Cost:** free
- **Tools:** read-only

This repository holds the public setup files: the MCP Registry listing, a Claude Code plugin and an agent skill. The server itself runs on calcupedia.io.

## What it does

Ask a calculation question and the assistant runs a real Calcupedia calculator instead of estimating. Finance, health, math, construction, physics, unit conversions and more, 2,400+ in total.

In Claude, the answer includes an **interactive calculator card**: inputs are prefilled from your question, and results update as you change any number. The card uses the same formulas as calcupedia.io, so the numbers always match the website.

## Tools

| Tool | What it does |
|---|---|
| `search_calculators` | Finds calculators and unit converters by keyword (for example "mortgage", "bmi", "kg to lbs"). The top results include their input names, defaults and allowed values. |
| `run_calculator` | Runs one calculator with your values and returns every result plus a link that opens it prefilled on calcupedia.io. In Claude, it also shows the live calculator card. |
| `get_embed_link` | For site owners: links to the page where you style a calculator and copy its embed code. |

All tools are read-only. They can't create accounts, change data or make purchases.

## Connect

### Claude (web, desktop and mobile)

1. Open **Customize → Connectors** and choose **Add custom connector**.
2. Paste `https://calcupedia.io/api/mcp` and save.
3. In a chat, turn it on under **+ → Connectors**.

Tip: start your message with "Using Calcupedia, ..." so Claude uses the calculators.

### Claude Code

```bash
claude mcp add --transport http calcupedia https://calcupedia.io/api/mcp
```

Or install the plugin from this repository, which adds the server plus a skill that tells Claude when to use it:

```
/plugin marketplace add OdehAhwal/calcupedia-mcp
/plugin install calcupedia@calcupedia
```

### Other MCP clients

Any client that supports remote Streamable HTTP servers can use `https://calcupedia.io/api/mcp`. A typical config:

```json
{
  "mcpServers": {
    "calcupedia": {
      "type": "http",
      "url": "https://calcupedia.io/api/mcp"
    }
  }
}
```

## Example prompts

- "Using Calcupedia, what's the monthly payment on a $400,000 mortgage at 6.5% for 30 years?"
- "Using Calcupedia, convert 5 ft 11 in to centimeters."
- "Using Calcupedia, how much concrete do I need for a 10 x 12 ft slab, 4 inches thick?"
- "Using Calcupedia, what's my BMI at 180 cm and 82 kg?"

## Privacy

Calcupedia logs the tool name, which calculator was used, which assistant sent the call and whether it succeeded. It does not store conversations, the values you enter, IP addresses or account details. Full policy: [calcupedia.io/privacy#mcp](https://calcupedia.io/privacy#mcp).

Results are estimates for general information, not financial, medical or legal advice.

## Support

Email [hi@odehahwal.com](mailto:hi@odehahwal.com) or open an issue in this repository.

## License

The files in this repository are MIT licensed. The Calcupedia service and its calculators are covered by the [Calcupedia terms](https://calcupedia.io/terms).
