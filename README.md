# Ransack

   Every SERP, every extractor. One MCP.

   Live search, page fetch and cited research for AI agents, from one MCP endpoint, with a source URL on every result and the finding engine named on every search result.

   **This is a hosted service.** This repository contains the connection configuration, documentation, and logo only; the server source is not public. Connect to:

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

   | Tool | What it does |
   |---|---|
   | `ransack` | The main tool. Modes: `search`, `fetch`, `discover`, `hosts`, `shop`, `verify`, `research`. Markdown / JSON / hybrid output. |
   | `youtube` | Fetch a YouTube transcript from a video URL. |
   | `execute_research` | Multi-step pipeline (discover, fetch, extract, synthesize) into a cited report with per-claim citation verdicts. |
   | `get_report` | Retrieve a persisted report by `report_id`. |
   | `search_memory` | Semantic recall over previously fetched page chunks. |
   | `tasks_get` | Poll an asynchronous research task. |
   | `ransack_permit_search` | US building permit lookup (currently Brevard County FL). Keyless, no browser, no captcha. |

   ### ransack
   One tool, many modes: `search`, `fetch`, `discover`, `hosts`, `shop`, `verify`, `research`.
   `search` is metasearch across engines; `fetch` is the primary answer path; `hosts` enumerates a domain's assets from certificate transparency, DNS, sitemaps, web archives, crawl indexes, JS routes and scan records; `shop` returns price and
 availability; `verify` checks a claim against its cited sources. `freshness` bypasses the result cache; it does not date-filter, so results are not filtered by date.

   ### youtube
   Fetch a YouTube transcript from a video URL.

   ### execute_research
   Multi-step pipeline (discover, fetch, extract, synthesize) into a cited report. Returns a task handle by default; poll `tasks_get` for the `report_id` and its per-claim citation verdicts.

   ### get_report
   Retrieve a persisted report by `report_id`.

   ### search_memory
   Semantic recall over previously fetched page chunks.

   ### tasks_get
   Poll an asynchronous research task.

   ### ransack_permit_search
   US building permit lookup (currently Brevard County FL). Keyless and captcha-free.

   ---

   ## What you actually get back

   - **Engine-tagged results.** Every search result names the engine that found it, so you can tell Google from an independent index.
   - **Coverage status, not silence.** On `hosts`, every discovery engine reports `ok`, `empty`, `timeout` or `skipped`. Found-nothing is never indistinguishable from tried-and-failed.
   - **Labelled walls.** `[bot wall: <vendor>]` and `[dead page: HTTP 404]` come back as labels. Pages the server cannot read are reported, not guessed.
   - **Per-claim citation verdicts.** Research reports carry a verdict per claim, checked against the sources actually retrieved.
   - **No query rewrites. Ever.** The caller owns site selection. Ransack never appends operators to your query or silently changes what you asked for.
   - **One key, seven tools.** Search, fetch, discovery, shopping, transcripts, permits and cited research behind a single endpoint.

   ---

   ## Honest limitations

   - Paywalled and login-walled pages (e.g. some news, GitHub `/commits` views) can't always be read.
   - Retailers that hard-block scraping (Amazon, Walmart) may return nothing rather than guessed data.
   - TikTok is searchable, and the result snippet already carries the caption. The reader tier returns the caption, creator handle, post date and engagement counts, but the video, the comments and the spoken transcript do not come back, and the browser
 tier can return only TikTok's "Page not available" stub.
   - `search` fast-lane results are partial by design; `fetch` is the primary answer path.
   - Labelling is not guaranteed: a wall sometimes comes back as thin page content instead.

   ---

   ## Pricing

   - **Trial:** free for 14 days, 50 calls/day, no card ([ransack.tools/trial](https://ransack.tools/trial)).
   - **Paid:** $15/month flat, 500 calls/day, 120 requests/min.

   ---

   ## License

   This repository is documentation and configuration only. The service at `ransack.tools` is proprietary.
