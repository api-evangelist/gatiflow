# GatiFlow

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

GatiFlow is a market, talent and hiring intelligence product that turns public developer activity into structured signals and serves them as a read-only JSON API. Thirteen public sources — GitHub, StackOverflow, HackerNews, Dev.to, arXiv, OpenReview, npm, PyPI, HuggingFace, Adzuna, Remotive, job boards (Greenhouse and Lever public postings) and SEC EDGAR — are polled on a six-hour cycle; a trend-category signal is published only once two independent sources confirm it or one source repeats it across two collection cycles, confidence is computed from source authority, diversity and persistence rather than raw mention count, and every signal carries its evidence and week-over-week movement. The public GatiFlow Intelligence API exposes seven read-only operations (the current report, snapshot history, a point-in-time snapshot, a CSV/PDF export, the daily insights payload, the latest Deep Dive preview, and per-key usage), authenticated with a gf_-prefixed API key in the X-API-Key header, priced across Free, Starter ($49/mo), Pro ($149/mo) and Business ($499/mo) plans.

**Areas:** Market Intelligence · Developer Signals · Trends · Hiring · Open Source · Research · B2B SaaS · Artificial Intelligence

## GatiFlow on APIs.io

Everything profiled for GatiFlow is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/gatiflow/](https://apis.io/providers/gatiflow/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [GatiFlow Intelligence API](https://apis.io/apis/gatiflow/gatiflow-intelligence-api/) — The intelligence operations of the GatiFlow Intelligence API — the current intelligence report (content scales with plan), snapshot history, one archived…
- [GatiFlow Public API](https://apis.io/apis/gatiflow/gatiflow-public-api/) — The public operations of the GatiFlow Intelligence API — the Daily Insights payload (web-app session auth, not an API key; an API key receives 401 there)…
- [GatiFlow Usage API](https://apis.io/apis/gatiflow/gatiflow-usage-api/) — The usage operation of the GatiFlow Intelligence API — recent calls made with the API key used on the request (limit up to 500), so a scheduled job can…
- [GatiFlow Webhooks API](https://apis.io/apis/gatiflow/gatiflow-webhooks-api/) — The intelligence:alert webhook GatiFlow pushes to HTTPS endpoints registered by Pro and Business organizations — spike, emerging and new_hirer alerts…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Gatiflow Webhooks](https://apis.io/asyncapis/gatiflow/gatiflow-webhooks/)

#### Event channels (1)

Individual events and webhooks the provider emits.

- [intelligenceAlert](https://apis.io/channels/gatiflow/intelligencealert/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [gatiflow-mcp.yml](https://apis.io/servers/gatiflow/gatiflow-mcp-yml/)

#### JSON Schema (5)

The data models the API reads and writes.

- [DailyInsights](https://apis.io/schemas/gatiflow/gatiflow-daily-insights/)
- [DeepDivePreview](https://apis.io/schemas/gatiflow/gatiflow-deep-dive-preview/)
- [IntelligenceReport](https://apis.io/schemas/gatiflow/gatiflow-intelligence-report/)
- [ReportHistory](https://apis.io/schemas/gatiflow/gatiflow-report-history/)
- [UsageLog](https://apis.io/schemas/gatiflow/gatiflow-usage-log/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Gatiflow Context](https://apis.io/jsonld/gatiflow/gatiflow-context/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Gatiflow Intelligence Api Phrasing Overlay](https://apis.io/overlays/gatiflow/gatiflow-intelligence-api-phrasing-overlay/)
- [Gatiflow Public Api Phrasing Overlay](https://apis.io/overlays/gatiflow/gatiflow-public-api-phrasing-overlay/)
- [Gatiflow Usage Api Phrasing Overlay](https://apis.io/overlays/gatiflow/gatiflow-usage-api-phrasing-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [GatiFlow API Rules](https://apis.io/rules/gatiflow/gatiflow-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Gatiflow Authentication](https://apis.io/security/gatiflow/gatiflow-authentication/)
- [Gatiflow Domain Security](https://apis.io/security/gatiflow/gatiflow-domain-security/)
- [Gatiflow Trust Center](https://apis.io/security/gatiflow/gatiflow-trust-center/)
- [Gatiflow Vulnerability Disclosure](https://apis.io/security/gatiflow/gatiflow-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Gatiflow Plans Pricing](https://apis.io/plans/gatiflow/gatiflow-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Gatiflow Rate Limits](https://apis.io/rate-limits/gatiflow/gatiflow-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Gatiflow Finops](https://apis.io/finops/gatiflow/gatiflow-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://gatiflow.io)
- [Getting started](https://gatiflow.io/api-docs)
- [Pricing](https://gatiflow.io/#pricing)
- [Changelog](https://gatiflow.io/changelog)
- [Blog](https://gatiflow.io/academy)
- [Security](https://gatiflow.io/aup)
- [Compliance](https://gatiflow.io/compliance)
- [Terms of service](https://gatiflow.io/terms)
- [Privacy policy](https://gatiflow.io/privacy)
- [Status](https://stats.uptimerobot.com/9fR5IzLq0q)

## API Evangelist rating

**Kin Score 95.3** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 91.1 |
| Contract quality | 76.4 |
| Contract governance | 96.7 |
| Operational transparency | 94.7 |
| Developer ergonomics | 75.5 |
| Access clarity | 100.0 |

**Agent readiness 59.3** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | unknown |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | verified |
| Event Surface Described | yes |
| Agent Skills | unknown |
| Well Known Catalog | yes |
| Consent Identity | yes |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 69.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/gatiflow/](https://apis.io/providers/gatiflow/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for GatiFlow: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/gatiflow/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
