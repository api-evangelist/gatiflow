---
name: gatiflow-weekly-intelligence
description: Pull the current GatiFlow market/talent intelligence report for your sector, export it for a warehouse or deck, walk retained snapshots for week-over-week movement, and check your API usage against plan limits.
api: openapi/gatiflow-openapi.yml
operations:
  - report_api_v1_intelligence_report_get
  - export_report_api_v1_intelligence_report_export_get
  - report_history_list_api_v1_intelligence_report_history_get
  - report_at_snapshot_api_v1_intelligence_report_at__snapshot_id__get
  - get_my_usage_api_v1_usage_get
method: generated
generated: '2026-09-21'
grounding: Every operationId above exists verbatim in openapi/gatiflow-openapi.yml. Auth, headers, quota and freshness rules are quoted from that contract and gatiflow.io/api-docs.
---

# Read GatiFlow weekly intelligence as an agent

The GatiFlow Intelligence API is read-only. Authenticate with an API key (prefix `gf_`) in the `X-API-Key` header; base URL is `https://api.gatiflow.io`. A daily call is enough — the report endpoint refuses to serve intelligence older than 24 hours.

## 1. Get the current report

`report_api_v1_intelligence_report_get` — `GET /api/v1/intelligence/report`. Returns the week filtered to the topics on your organization profile. Read `trend_analysis` (`velocity`, `spikes`, `emerging`, `declining`) for movement and `sections.market_trends` for topics your buyers are reading about. Report depth scales with plan (signal, trend and talent caps).

- If the report is stale, the endpoint returns **503 with `Retry-After`** — back off and retry after that interval, do not hammer it.
- Watch `X-RateLimit-*` and `X-DailyQuota-*` response headers; the per-minute rate and daily quota are set by plan (Free 5/min·10/day, Starter 60/min·2,000/day, Pro 120/min·10,000/day, Business 300/min·50,000/day).

## 2. Export it for a warehouse or deck

`export_report_api_v1_intelligence_report_export_get` — `GET /api/v1/intelligence/report/export?format=csv` (Pro/Business) or `format=pdf` (Business only). Same report as a file. A 422 means the `format` parameter is invalid or unavailable on your plan.

## 3. Walk history for week-over-week movement

`report_history_list_api_v1_intelligence_report_history_get` — `GET /api/v1/intelligence/report-history?limit=N` (N is 1–50; Free excluded). Snapshot ids come back in `YYYYMMDDTHHmm` format. Fetch any one with `report_at_snapshot_api_v1_intelligence_report_at__snapshot_id__get` — `GET /api/v1/intelligence/report/at/{snapshot_id}`. These consume no daily quota (rate-limited only), so a dashboard can backfill history cheaply.

## 4. Stay inside your limits

`get_my_usage_api_v1_usage_get` — `GET /api/v1/usage?limit=N` (default 100, max 500). Shows the recent calls made with this API key so a scheduled job can self-audit before it trips the quota.

## Errors

Errors use a custom envelope `{ "status": "error", "error": { "message", "code", "http_status", "request_id" } }` (not RFC 9457). A `401` means the key is missing/invalid or you called a session-only operation with an API key. Keep the `request_id` for support.
