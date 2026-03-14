# MorningKatie

**Katie** is an open-source Claude Code agent that connects to the [Green Invoice (Morning)](https://www.greeninvoice.co.il) API via MCP. She handles the full accounting and invoicing workflow — invoices, receipts, proposals, shipping slips, credit notes, expenses, clients, and products.

---

## What Katie Does

- Create and manage invoices, receipts, proposals, shipping slips, and credit notes
- Search and manage clients and products/catalog items
- Log and search expenses
- Run a morning accounting summary (open invoices, overdue, expenses)
- Works in Hebrew and English

---

## Requirements

- [Claude Code](https://claude.ai/code) (CLI)
- A [Green Invoice](https://app.greeninvoice.co.il) account (production or sandbox)
- The `mcp-green-invoice` MCP server (npm package)

---

## Quick Setup

### 1. Install the MCP server

```bash
npm install -g mcp-green-invoice
```

### 2. Generate a Green Invoice API key

1. Log into your Green Invoice dashboard
2. Go to **Settings → API**
3. Click **Generate API Key** — save the `KEY_ID` and `KEY_SECRET` (the secret is shown only once)

### 3. Configure Claude Code

Edit `~/.claude/settings.json`:

```json
{
  "mcpServers": {
    "green-invoice": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-green-invoice/index.js"],
      "env": {
        "GREEN_INVOICE_KEY_ID": "your-key-id-here",
        "GREEN_INVOICE_KEY_SECRET": "your-secret-here"
      }
    }
  }
}
```

> If your secret contains a `"` character, escape it as `\"` in the JSON.

Fully restart Claude Code after saving — the MCP server loads env vars at startup only.

### 4. Add Katie to your agent setup

Copy `katie-agent.md` into your Claude Code project folder and reference it in your `CLAUDE.md` or session instructions.

### 5. Test the connection

Ask Katie: **"Katie, get my business info"**

A successful response returns your business name, tax ID, and VAT settings.

---

## Usage Examples

```
Katie, send an invoice to [client] for [amount]
Katie, send a proposal to [client]
Katie, create a shipping slip for [order]
Katie, issue a credit note for invoice #[X]
Katie, log an expense
Katie, show me all invoices this month
Katie, morning routine
```

---

## File Structure

```
MorningKatie/
├── README.md          — This file
├── katie-agent.md     — Agent definition (drop into your Claude Code project)
└── DISCLAIMER.md      — Terms of use and MIT license
```

---

## Disclaimer

See [DISCLAIMER.md](./DISCLAIMER.md) for full terms.

**In short:** This software is provided as-is, with no warranty of any kind. The author accepts zero responsibility for any financial, legal, tax, or accounting consequences arising from its use.

---

## Credits

Created by **Michael S.**

---

## License

MIT — free to use, modify, and distribute. See [DISCLAIMER.md](./DISCLAIMER.md).
