# Sequence (sequence-hq)

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

Sequence is a usage-based billing, pricing, and revenue orchestration platform for B2B SaaS and other recurring-revenue businesses. It turns product usage and negotiated contract terms into automated billing schedules, invoices, credit notes, and quotes, backed by a metering engine for usage events and usage metrics, plus revenue recognition and integrations to ERP/CRM, tax, and payment providers.

## Access Model (read this first)

- **Real, documented REST API.** Sequence publishes a resource-based REST API at `https://docs.sequencehq.com` designed "similar in spirit to Stripe's."
- **Base host:** `https://eu.sequencehq.com` (Production, EU). A **Sandbox** environment mirrors it at `https://sandbox.sequencehq.com`. Usage ingestion is served under the `/api/` prefix (`POST /api/usage-events`); most resource operations are at the host root (`/customers`, `/invoices`, ...).
- **Authentication:** HTTP **Basic auth** — Client ID (username) and Client Secret (password), created in the Sequence Dashboard (the secret is shown once). Not a Bearer token.
- **Versioning:** date-based, selected with the `sequence-version` header (for example `2024-07-30`) or the `latest` alias.
- **Events:** outbound **webhooks** (signed HTTP POST callbacks, `Sequence-Signature` HMAC-SHA256). **No WebSocket / `wss://` API is documented.**
- **Honesty note:** the following operations were confirmed directly against the live API reference (host + path): `GET /customers`, `POST /api/usage-events`, `GET /billing-schedules`, `GET /invoices`, `GET /products`. Every other operation in the OpenAPI and collections here is a **real, documented operation** whose exact path spelling and request/response schema are **modeled** and flagged with `x-modeled: true`. Verify payloads against `docs.sequencehq.com` before production use.

> Disambiguation: this is **Sequence the billing/revenue platform** at sequencehq.com — **not** the web3 wallet "Sequence" (sequence.xyz / 0xsequence) and **not** the personal-finance money-routing app at getsequence.io.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/sequence-hq/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/sequence-hq/refs/heads/main/apis.yml)

## Tags

- Billing
- Usage-Based Billing
- Revenue Recognition
- Metering
- Invoicing
- Pricing
- Revenue Orchestration
- FinOps

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Sequence Customers API

Create, retrieve, update, archive, and list customers, along with their contacts, customer aliases (external IDs used to attribute usage), and customer organizations. Customers are the billable entities that billing schedules, invoices, and usage events attach to.

- **Human URL:** [https://docs.sequencehq.com/reference/latest/customer/list-customers](https://docs.sequencehq.com/reference/latest/customer/list-customers)
- **Base URL:** `https://eu.sequencehq.com`

#### Tags

- Customers
- Contacts
- Billing

#### Properties

- [Documentation](https://docs.sequencehq.com/reference/gettingStarted)
- [API Reference](https://docs.sequencehq.com/reference/latest/customer/list-customers)
- [OpenAPI](openapi/sequence-hq-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sequence-hq.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sequence-hq.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sequence Usage & Metering API

Ingest usage events (`POST /api/usage-events`) keyed by `customerAlias` and `eventType`, define and manage usage metrics that aggregate those events, calculate a metric for a customer over a timeframe, and manage seat metrics and seat events for seat-based billing. This is the metering foundation for usage-based pricing, with a higher dedicated rate limit for ingestion.

- **Human URL:** [https://docs.sequencehq.com/reference/latest/usage/create-a-new-usage-event](https://docs.sequencehq.com/reference/latest/usage/create-a-new-usage-event)
- **Base URL:** `https://eu.sequencehq.com`

#### Tags

- Usage-Based Billing
- Metering
- Events

#### Properties

- [API Reference](https://docs.sequencehq.com/reference/latest/usage/create-a-new-usage-event)
- [OpenAPI](openapi/sequence-hq-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sequence-hq.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sequence-hq.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sequence Billing Schedules API

Create, activate, archive, duplicate, retrieve, update, and list billing schedules — the recurring contract terms that translate a customer's negotiated pricing into automatically generated invoices over time. Includes tax validation on a billing schedule.

- **Human URL:** [https://docs.sequencehq.com/reference/latest/billing/list-all-billing-schedules](https://docs.sequencehq.com/reference/latest/billing/list-all-billing-schedules)
- **Base URL:** `https://eu.sequencehq.com`

#### Tags

- Billing
- Subscriptions
- Contracts

#### Properties

- [API Reference](https://docs.sequencehq.com/reference/latest/billing/list-all-billing-schedules)
- [OpenAPI](openapi/sequence-hq-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sequence-hq.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sequence-hq.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sequence Invoices & Credit Notes API

Manage the accounts-receivable lifecycle — create, retrieve, update, patch, finalize, send, void, and delete invoices, manage line items and line item groups, download invoice PDFs, and issue credit notes against invoices. Covers draft-to-sent transitions, payment reminders, and payment status updates.

- **Human URL:** [https://docs.sequencehq.com/reference/latest/invoices/list-all-invoices](https://docs.sequencehq.com/reference/latest/invoices/list-all-invoices)
- **Base URL:** `https://eu.sequencehq.com`

#### Tags

- Invoicing
- Credit Notes
- Accounts Receivable

#### Properties

- [API Reference](https://docs.sequencehq.com/reference/latest/invoices/list-all-invoices)
- [OpenAPI](openapi/sequence-hq-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sequence-hq.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sequence-hq.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sequence Products & Prices API

Manage the product and pricing catalog — create, retrieve, update, and archive products; create, retrieve, update, and delete prices; and manage reusable list prices. Pricing models support flat, per-unit, tiered, and usage-based structures that feed billing schedules and quotes.

- **Human URL:** [https://docs.sequencehq.com/reference/latest/product/list-all-products](https://docs.sequencehq.com/reference/latest/product/list-all-products)
- **Base URL:** `https://eu.sequencehq.com`

#### Tags

- Pricing
- Products
- Catalog

#### Properties

- [API Reference](https://docs.sequencehq.com/reference/latest/product/list-all-products)
- [OpenAPI](openapi/sequence-hq-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sequence-hq.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sequence-hq.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sequence Quotes API

List quotes, retrieve quote analytics, and download quote PDFs. Quotes capture negotiated deal terms (products, prices, discounts) that, once signed and accepted, convert into billing schedules — the quote-to-revenue path for sales-led usage-based businesses.

- **Human URL:** [https://docs.sequencehq.com/reference/latest/quote/list-quotes](https://docs.sequencehq.com/reference/latest/quote/list-quotes)
- **Base URL:** `https://eu.sequencehq.com`

#### Tags

- Quotes
- CPQ
- Revenue Orchestration

#### Properties

- [API Reference](https://docs.sequencehq.com/reference/latest/quote/list-quotes)
- [OpenAPI](openapi/sequence-hq-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sequence-hq.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sequence-hq.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Domain Security](security/sequence-hq-domain-security.yml)
- [Authentication](authentication/sequence-hq-authentication.yml)
- [GitHub Organization](https://github.com/sequencehq)
- [LinkedIn](https://www.linkedin.com/company/sequence-hq)
- [Website](https://www.sequencehq.com)
- [Documentation](https://docs.sequencehq.com)
- [Plans](plans/sequence-hq-plans-pricing.yml)
- [Rate Limits](rate-limits/sequence-hq-rate-limits.yml)
- [Fin Ops](finops/sequence-hq-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
