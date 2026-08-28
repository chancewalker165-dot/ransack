# Ransack

Live search, page fetch, and cited research for AI agents — one MCP endpoint with source-attributed answers.

**This is a hosted service.** This repository contains the connection configuration, documentation, and logo only — the server source is not public. Connect to:

```
https://ransack.tools/mcp
```

- Homepage: [ransack.tools](https://ransack.tools)
- Free trial key: [ransack.tools/trial](https://ransack.tools/trial)

---

## Connect

Get an API key from [ransack.tools/trial](https://ransack.tools/trial), then add the server to your client.

**Claude Desktop**

```json
{"mcpServers":{"ransack":{"type":"streamable-http","url":"https://ransack.tools/mcp","headers":{"Authorization":"Bearer <API_KEY>"}}}}
```

**Cursor**

```json
{"mcpServers":{"ransack":{"url":"https://ransack.tools/mcp","headers":{"Authorization":"Bearer <API_KEY>"}}}}
```

**Pi / Cline / 5ire**

```json
{"mcpServers":{"ransack":{"type":"http","url":"https://ransack.tools/mcp","headers":{"Authorization":"Bearer <API_KEY>"}}}}
```

Transport is `streamable-http`; authentication is a Bearer API key.

---

## Tools

### ransack
One tool, many modes: `search`, `fetch`, `discover`, `hosts`, `verify`, `research`. Markdown / JSON / hybrid output, recency filter, source-attributed and deduplicated results.

### execute_research
Multi-step pipeline (discover → fetch → extract → synthesize) into a cited report.

### get_report
Retrieve a persisted report by `report_id`.

### search_memory
Semantic recall over previously fetched page chunks.

### tasks_get
Poll an asynchronous research task.

### ransack_permit_search
US building-permit lookup (currently Brevard County FL).

Every result carries a source URL. Pages the server can't read — login-walled pages, bot-blocked retailers — are reported as limitations rather than silently skipped.

---

## Honest limitations

- Paywalled and login-walled pages (e.g. some news, GitHub `/commits` views) can't always be read.
- Retailers that hard-block scraping (Amazon, Walmart, TikTok) may return nothing rather than guessed data.
- `search` fast-lane results are partial by design; `fetch` is the primary answer path.

---

## Pricing

- **Trial:** free (sign up at [ransack.tools/trial](https://ransack.tools/trial)).
- **Paid:** plans are opening once billing is verified.

---

## License

This repository is documentation and configuration only. The service at `ransack.tools` is proprietary.
