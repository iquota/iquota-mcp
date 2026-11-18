# iQuota Hotels — MCP server

Remote MCP server for booking independent hotels, apartments and villas
that are contracted directly with their owners. No commission for the
property; the traveller pays at the property.

- Server name in the MCP Registry: `io.iquota/hotels`
- Endpoint (Streamable HTTP, no sign-in): `https://iquota.io/mcp`
- Endpoint with OAuth 2.1: `https://iquota.io/connect/mcp`
- More information: https://iquota.io/ai

This repository only documents the hosted server; the server itself is
operated by iQuota and its source code is not published here.

## Tools

| Tool | What it does |
|---|---|
| `search_hotels` | Search by destination, dates and guests; live availability and prices |
| `get_hotel` | Property details, the property's own photos, policies |
| `check_rate` | Re-quote a rate before booking (final price, cancellation, payment terms) |
| `book_hotel` | Book after the traveller has explicitly confirmed |
| `get_booking` | Look up a booking |
| `cancel_booking` | Cancel a booking under the property's cancellation policy |

## Configuration

Add it as a remote MCP server in your client, for example in VS Code
(`.vscode/mcp.json`):

```json
{
  "servers": {
    "iquota-hotels": { "type": "http", "url": "https://iquota.io/mcp" }
  }
}
```

In Claude or ChatGPT, add a custom connector with the URL `https://iquota.io/mcp`.

## Usage

Ask your assistant, for example: "Find a house for 4 in Atlanterra
from 10 to 14 June 2027". Typical flow: `search_hotels` → `get_hotel`
→ `check_rate` → `book_hotel`. Before booking, the assistant must show
the property, dates, total price, cancellation policy and payment terms
and get the traveller's confirmation. Never ask the traveller for card
details: payment is collected by the property.

## Contact

hello@iquota.io · https://iquota.io
