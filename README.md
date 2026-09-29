# Plendio extension for Gemini CLI

Adds the public [Plendio](https://plendio.com) MCP server to the Gemini CLI: price comparison and product
search for shoppers in Denmark, Sweden, Germany and Norway. Ask for a product, compare shop prices
including shipping, read specifications and price history, and see which shops deliver to your country.

The extension is one connection to a hosted server; there is nothing to build or run locally.

## Install

```sh
gemini extensions install https://github.com/dsjacobsen/plendio-gemini
```

Restart the Gemini CLI and run `/mcp` to check that the `plendio` server is connected with four tools.
No sign-in, API key or settings are needed.

## Tools

All four tools are read-only and only read Plendio's own product catalogue.

| Tool | What it does |
|---|---|
| `search_products` | Search products by free text (Danish, Swedish, German, Norwegian or English) with optional filters |
| `get_product` | Specifications, one offer per shop and price history of one product |
| `compare_prices` | The shops selling one product, cheapest first including shipping |
| `list_categories` | Product categories with localized names and product counts |

Example prompts:

- Find a laptop with 32 GB RAM under 12,000 kr.
- Where is the Sony WH-1000XM5 cheapest in Sweden, including shipping?
- Is now a good time to buy the Samsung Galaxy S25 256 GB?
- What categories of electronics do you have, and how many products in each?

## What it sends

The extension registers `https://plendio.com/mcp` as a streamable HTTP MCP server. Gemini CLI sends the
arguments of a tool call (for example the search text and the market) to that address; Plendio never sees
the rest of your conversation. There are no cookies and no accounts. The server logs the tool name, market,
query text, result count, outcome, duration, the client's name and version, its user agent and a keyed
hash of the client address that cannot be turned back into an address. The full policy is at
https://plendio.dk/privacy.

## Notes

- Prices are the shops' own, collected from their product feeds and public shop APIs, and change during
  the day. Plendio may earn a commission when you buy after clicking through to a shop; results contain
  no advertising and the commission does not change their order (https://plendio.dk/how-we-rank).
- Rate limit: 120 tool calls per minute and 20,000 per day per client address.
- Documentation: https://plendio.dk/ai

## Support

hello@plendio.com. Plendio is operated by PriceBot ApS, Denmark.

## Licence

MIT, see [LICENSE](LICENSE).
