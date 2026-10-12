---
name: gatiflow-intelligence
description: Read GatiFlow's market, talent and hiring intelligence through its API with an API key - fetch the organization's current report, walk retained snapshots for movement instead of calling again, export the report as a file, and check what a key has used - and report confidence, corroboration and trend movement without overstating them. Use when a task needs developer-ecosystem signals (trending technologies, papers, packages, talent, hiring) from GatiFlow.
license: Proprietary. Use of the API and of its outputs is governed by https://gatiflow.io/terms and https://gatiflow.io/aup.
compatibility: Needs HTTPS access to api.gatiflow.io and a GatiFlow API key (prefix gf_), here read from the GATIFLOW_API_KEY environment variable.
metadata:
  publisher: GatiFlow
  method: published
  source: https://gatiflow.io/.well-known/agent-skills/gatiflow-intelligence/SKILL.md
  contract: https://gatiflow.io/openapi.json
  vocabulary: https://gatiflow.io/vocabulary.json
---

# GatiFlow intelligence

GatiFlow turns public developer activity into market, talent and hiring signals and serves them as a read-only JSON API at `https://api.gatiflow.io`. The contract is https://gatiflow.io/openapi.json: when this file and the contract disagree, the contract is right. Every term used below is defined in https://gatiflow.io/vocabulary.json.

## Before the first call

- Every operation here reads. None writes, and none needs a person to approve it; the `x-agentic-access` block on each operation in the contract says so.
- Send the key in the `X-API-Key` header. Never put it in a URL, a log line or a message shown to anyone.
- Limits belong to the organization, not to the key: every key it holds draws on one per-minute rate limit and one daily quota.
- Only the report and the export consume daily quota. History and a snapshot consume none but count against the per-minute limit, as the report and the export do. Reading the usage log does neither.

## Get the current report

`GET /api/v1/intelligence/report`

```bash
curl -s -H "X-API-Key: $GATIFLOW_API_KEY" \
  "https://api.gatiflow.io/api/v1/intelligence/report?schema_version=1.2"
```

- One call a day is enough. The data changes when the collection cycle runs, every six hours, and each successful call costs one unit of quota.
- `schema_version=1.2` returns the plan contract with its capabilities and limits; the default, 1.0, is compact.
- The signals are in `sections.market_trends`, `sections.talent_signals` and `sections.hiring_signals`. Movement is in `trend_analysis`: `velocity`, `spikes`, `emerging` and `declining`.
- A 503 with `Retry-After` means the newest data is more than 24 hours old. Wait the seconds it gives before asking again, and never present an older report as current.
- A 429 means the per-minute limit or the daily quota is spent; `error.message` says which. Successful responses carry `X-RateLimit-Remaining` and `X-DailyQuota-Remaining`: stop before they reach 0. A request refused by the per-minute limit succeeds once `X-RateLimit-Reset-Seconds` have passed.

## Read history instead of calling again

- `GET /api/v1/intelligence/report-history?limit=N` (1 to 50) lists the retained snapshots, newest first. Each has a `snapshot_id` in the `YYYYMMDDTHHmm` format. A plan without history gets an empty list.
- `GET /api/v1/intelligence/report/at/{snapshot_id}` returns one snapshot in the same shape as the report. A malformed id gets 400, an id outside the plan's retention window 404, and a plan with no history 403.
- To compare weeks, read snapshots. Calling the report again spends quota, and within one collection cycle it returns the same data.

## Export a file

`GET /api/v1/intelligence/report/export?format=csv` on Pro and Business, `format=pdf` on Business. The body is the file itself. A format the plan does not include gets 403. An export consumes one unit of quota, like a report.

## Check what a key has used

`GET /api/v1/usage?limit=N` lists the reports and exports fetched with this key, newest first: 100 by default, never more than 500. It belongs to the key, and a refused call or a call to any other operation leaves no entry, so it is not a full request log.

## Report the numbers honestly

- Confidence runs from 0 to 1 and says how strong and how well supported a signal is now. It is not a forecast: never present it as the probability that a trend continues.
- A trend signal is published only once two independent sources confirm it, or one source repeats it across two collection cycles. A single mention never reaches the report.
- `change_pct` is null while a topic has no baseline. Say "no baseline yet", not "0%".
- `metadata.ai_generated` names the parts a language model wrote, such as the executive summary's narrative. Quote them as commentary, not as measurement.
- Talent signals describe public developer profiles. They are a starting point for qualified outreach, never the sole basis for a hiring decision.

## Errors

Every refusal has one envelope: `status` is `error`, and `error` carries `message`, `code`, `http_status`, `request_id` and `details`. `error.code` is `NOT_FOUND` for a 404, `VALIDATION_ERROR` for a 422 (each problem listed in `error.details`), `INTERNAL_ERROR` for a 500 and `HTTP_ERROR` otherwise. Keep `error.request_id`, also sent as the `X-Request-ID` header, for support@gatiflow.io.

- 401: the key is missing, unknown, revoked or expired.
- 402: the organization has no subscription, or it is not active.
- 403: the organization is inactive, its owner's email address is unverified, the key lacks the `intelligence:read` scope, or the plan does not include what was asked for.

## Not for an API key

- `GET /api/v1/public/deep-dive` takes no credential. It returns the preview of the latest weekly Deep Dive and the address of the full article, which is free to read. It is capped per caller address and answers 429 past the cap.
- `GET /api/v1/public/weekly-report`, the Daily Insights payload, takes the web-app session. An API key gets 401 there, so do not call it with one.

## Webhooks

On Pro and Business an organization can register an HTTPS endpoint in Settings to receive `intelligence:alert` events. Verify `X-GatiFlow-Signature` (the HMAC-SHA256 of `<timestamp>.<raw body>` under the webhook secret) before acting on a delivery, and use `X-GatiFlow-Delivery-Id` to drop the duplicates retries produce. Details: https://gatiflow.io/api-docs/webhooks.
