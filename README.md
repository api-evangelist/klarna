# Klarna

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

Klarna Bank AB is a Swedish licensed bank and payments network serving 150M+ consumers and 600k+ merchants with buy-now-pay-later, financing, cards, banking and a shopping app. For developers Klarna publishes a merchant API estate covering payment sessions and authorization (Klarna Payments), hosted checkout (Klarna Checkout and the Hosted Payment Page), post-purchase order management (capture, refund, cancel, extend due date), customer tokens for recurring purchases, settlement payouts and transaction reporting, the Merchant Card Service, and a PSD2 XS2A open-banking API for licensed TPPs. Authentication is HTTP Basic with a Klarna-issued API key; Sign in with Klarna adds a full OAuth 2.0 / OpenID Connect consumer-identity surface. Klarna publishes rate limits, a six-month deprecation policy, public service-level objectives, a self-serve playground with market-specific sample data, and an llms.txt — but no fetchable OpenAPI, no server-side SDK in any language, and no MCP server.

**Areas:** Fintech · Buy Now Pay Later · Payments · Cards · Shopping · Banking · Checkout · Order Management · Settlement · Open Banking · PSD2 · Consumer Credit

## Klarna on APIs.io

Everything profiled for Klarna is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/klarna/](https://apis.io/providers/klarna/)** — or go straight to one of the APIs or properties below.

### APIs (22)

- [Klarna Payments API](https://apis.io/apis/klarna/klarna-payments-api-2/) — Create and authorize Klarna payment sessions; create orders against authorizations.
- [Klarna Checkout API](https://apis.io/apis/klarna/klarna-checkout-api-2/) — Hosted Klarna Checkout (KCO), the checkout/v3 surface. Klarna divested the Klarna Checkout product and it now trades as Kustom; as of 2026-08-27 Klarna no…
- [Klarna Order Management API](https://apis.io/apis/klarna/klarna-order-management-api/) — Capture, refund, cancel and update orders post-authorization.
- [Klarna Customer Token API](https://apis.io/apis/klarna/klarna-customer-token-api-2/) — Persist a payment authorization as a customer token for repeat purchases.
- [Klarna Settlements API](https://apis.io/apis/klarna/klarna-settlements-api/) — Read merchant settlement reports and transactions.
- [Klarna Push Notifications](https://apis.io/apis/klarna/klarna-push-notifications/) — Outbound HTTP POST callbacks Klarna issues to merchant-hosted URLs for Payments authorization, HPP status updates, Checkout push, and pending-order risk…
- [Klarna Captures API](https://apis.io/apis/klarna/klarna-captures-api/) — The Captures API from Klarna — 6 operation(s) for captures.
- [Klarna Checkout API](https://apis.io/apis/klarna/klarna-checkout-api/) — The Checkout API from Klarna — 3 operation(s) for checkout.
- [Klarna Customer Token API](https://apis.io/apis/klarna/klarna-customer-token-api/) — The Customer Token API from Klarna — 3 operation(s) for customer token.
- [Klarna Hpp API](https://apis.io/apis/klarna/klarna-hpp-api/) — The Hpp API from Klarna — 3 operation(s) for hpp.
- [Klarna Merchant Urls.address Update API](https://apis.io/apis/klarna/klarna-merchant-urls-address-update-api/) — The Merchant Urls.address Update API from Klarna — 1 operation(s) for merchant urls.address update.
- [Klarna Merchant Urls.country Change API](https://apis.io/apis/klarna/klarna-merchant-urls-country-change-api/) — The Merchant Urls.country Change API from Klarna — 1 operation(s) for merchant urls.country change.
- [Klarna Merchant Urls.shipping Option Update API](https://apis.io/apis/klarna/klarna-merchant-urls-shipping-option-update-api/) — The Merchant Urls.shipping Option Update API from Klarna — 1 operation(s) for merchant urls.shipping option update.
- [Klarna Merchant Urls.validation API](https://apis.io/apis/klarna/klarna-merchant-urls-validation-api/) — The Merchant Urls.validation API from Klarna — 1 operation(s) for merchant urls.validation.
- [Klarna Orders API](https://apis.io/apis/klarna/klarna-orders-api/) — The Orders API from Klarna — 9 operation(s) for orders.
- [Klarna Payments API](https://apis.io/apis/klarna/klarna-payments-api/) — The Payments API from Klarna — 5 operation(s) for payments.
- [Klarna Payouts API](https://apis.io/apis/klarna/klarna-payouts-api/) — The Payouts API from Klarna — 3 operation(s) for payouts.
- [Klarna Refunds API](https://apis.io/apis/klarna/klarna-refunds-api/) — The Refunds API from Klarna — 2 operation(s) for refunds.
- [Klarna Reports API](https://apis.io/apis/klarna/klarna-reports-api/) — The Reports API from Klarna — 4 operation(s) for reports.
- [Klarna Transactions API](https://apis.io/apis/klarna/klarna-transactions-api/) — The Transactions API from Klarna — 1 operation(s) for transactions.
- [Klarna Agentic Product Protocol (KAPP) API](https://apis.io/apis/klarna/klarna-agentic-product-protocol-kapp-api/) — Klarna's agent-facing product protocol, exposing product and commerce data for AI agents to query. Registered 2026-09-04 from the same declined submission.
- [Klarna Merchant Card API](https://apis.io/apis/klarna/klarna-merchant-card-api/) — The Merchant Card API from Klarna — 6 operation(s) for merchant card.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Klarna Push Notifications](https://apis.io/asyncapis/klarna/klarna-push-notifications-asyncapi/)

#### Event channels (4)

Individual events and webhooks the provider emits.

- [checkout/push](https://apis.io/channels/klarna/checkout-push/)
- [payments/authorization-callback](https://apis.io/channels/klarna/payments-authorization-callback/)
- [payments/hpp-status-update](https://apis.io/channels/klarna/payments-hpp-status-update/)
- [payments/pending-order-notification](https://apis.io/channels/klarna/payments-pending-order-notification/)

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/klarna/](https://apis.io/graphqls/klarna/klarna-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [klarna](https://apis.io/servers/klarna/klarna/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Klarna Agentic Access](https://apis.io/agentic-access/klarna/klarna-agentic-access/)

#### JSON Schema (86)

The data models the API reads and writes.

- [Addon](https://apis.io/schemas/klarna/klarna-addon/)
- [Address](https://apis.io/schemas/klarna/klarna-address/)
- [BackgroundImageV1](https://apis.io/schemas/klarna/klarna-backgroundimagev1/)
- [Cancel not allowed error message](https://apis.io/schemas/klarna/klarna-cancel-not-allowed-error-message/)
- [cancel_order_request_status](https://apis.io/schemas/klarna/klarna-cancel-order-request-status/)
- [cancel_order_request_status_cancelled](https://apis.io/schemas/klarna/klarna-cancel-order-request-status-cancelled/)
- [cancel_order_request_status_no_request_found](https://apis.io/schemas/klarna/klarna-cancel-order-request-status-no-request-found/)
- [cancel_order_request_status_pending](https://apis.io/schemas/klarna/klarna-cancel-order-request-status-pending/)
- [Capture](https://apis.io/schemas/klarna/klarna-capture/)
- [Capture not allowed error message](https://apis.io/schemas/klarna/klarna-capture-not-allowed-error-message/)
- [CaptureObject](https://apis.io/schemas/klarna/klarna-capture-object/)
- [CaptureObject](https://apis.io/schemas/klarna/klarna-captureobject/)
- [card](https://apis.io/schemas/klarna/klarna-card/)
- [card_specification](https://apis.io/schemas/klarna/klarna-card-specification/)
- [CarrierProduct](https://apis.io/schemas/klarna/klarna-carrierproduct/)
- [create_order_request](https://apis.io/schemas/klarna/klarna-create-order-request/)
- [customer](https://apis.io/schemas/klarna/klarna-customer/)
- [customer_token](https://apis.io/schemas/klarna/klarna-customer-token/)
- [customer_token_creation_response](https://apis.io/schemas/klarna/klarna-customer-token-creation-response/)
- [customer_token_order](https://apis.io/schemas/klarna/klarna-customer-token-order/)
- [customer_token_status_update_request](https://apis.io/schemas/klarna/klarna-customer-token-status-update-request/)
- [CustomerV1](https://apis.io/schemas/klarna/klarna-customerv1/)
- [DistributionRequestV1](https://apis.io/schemas/klarna/klarna-distribution-request-v1/)
- [DistributionContactV1](https://apis.io/schemas/klarna/klarna-distributioncontactv1/)
- [DistributionModuleV1](https://apis.io/schemas/klarna/klarna-distributionmodulev1/)
- …and 61 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Klarna Context](https://apis.io/jsonld/klarna/klarna-context/)

#### Collections (19)

Postman and Open Collection request collections.

- [Klarna HPP](https://apis.io/collections/klarna/open-hosted-payment-page-api/)
- [Klarna HPP Captures API](https://apis.io/collections/klarna/open-klarna-captures-api/)
- [Klarna HPP Captures Checkout API](https://apis.io/collections/klarna/open-klarna-checkout-api/)
- [Klarna HPP Captures Customer Token API](https://apis.io/collections/klarna/open-klarna-customer-token-api/)
- [Klarna Captures Hpp API](https://apis.io/collections/klarna/open-klarna-hpp-api/)
- [Klarna HPP Captures Merchant Urls.address Update API](https://apis.io/collections/klarna/open-klarna-merchant-urls-address-update-api/)
- [Klarna HPP Captures Merchant Urls.country Change API](https://apis.io/collections/klarna/open-klarna-merchant-urls-country-change-api/)
- [Klarna HPP Captures Merchant Urls.shipping Option Update API](https://apis.io/collections/klarna/open-klarna-merchant-urls-shipping-option-update-api/)
- [Klarna HPP Captures Merchant Urls.validation API](https://apis.io/collections/klarna/open-klarna-merchant-urls-validation-api/)
- [Klarna HPP Captures Merchantcard API](https://apis.io/collections/klarna/open-klarna-merchantcard-api/)
- [Klarna HPP Captures Orders API](https://apis.io/collections/klarna/open-klarna-orders-api/)
- [Klarna HPP Captures Payments API](https://apis.io/collections/klarna/open-klarna-payments-api/)
- [Klarna HPP Captures Payouts API](https://apis.io/collections/klarna/open-klarna-payouts-api/)
- [Klarna HPP Captures Refunds API](https://apis.io/collections/klarna/open-klarna-refunds-api/)
- [Klarna HPP Captures Reports API](https://apis.io/collections/klarna/open-klarna-reports-api/)
- [Klarna Settlements API](https://apis.io/collections/klarna/open-klarna-settlements-api/)
- [Klarna HPP Captures Transactions API](https://apis.io/collections/klarna/open-klarna-transactions-api/)
- [Klarna Merchant Card Service API](https://apis.io/collections/klarna/open-merchant-card-service-api/)
- [Klarna Order Management API](https://apis.io/collections/klarna/open-order-management-api/)

#### Overlays (30)

OpenAPI overlays, including conversational phrasing for each operation.

- [Klarna Captures Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-captures-api-phrasing-overlay/)
- [Klarna Captures Overlay](https://apis.io/overlays/klarna/klarna-captures-overlay/)
- [Klarna Checkout Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-checkout-api-phrasing-overlay/)
- [Klarna Checkout Overlay](https://apis.io/overlays/klarna/klarna-checkout-overlay/)
- [Klarna Customer Token Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-customer-token-api-phrasing-overlay/)
- [Klarna Customer Token Overlay](https://apis.io/overlays/klarna/klarna-customer-token-overlay/)
- [Klarna Hpp Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-hpp-api-phrasing-overlay/)
- [Klarna Hpp Overlay](https://apis.io/overlays/klarna/klarna-hpp-overlay/)
- [Klarna Merchant Card Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-merchant-card-api-phrasing-overlay/)
- [Klarna Merchant Urls Address Update Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-address-update-api-phrasing-overlay/)
- [Klarna Merchant Urls Address Update Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-address-update-overlay/)
- [Klarna Merchant Urls Country Change Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-country-change-api-phrasing-overlay/)
- [Klarna Merchant Urls Country Change Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-country-change-overlay/)
- [Klarna Merchant Urls Shipping Option Update Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-shipping-option-update-api-phrasing-overlay/)
- [Klarna Merchant Urls Shipping Option Update Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-shipping-option-update-overlay/)
- [Klarna Merchant Urls Validation Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-validation-api-phrasing-overlay/)
- [Klarna Merchant Urls Validation Overlay](https://apis.io/overlays/klarna/klarna-merchant-urls-validation-overlay/)
- [Klarna Merchantcard Overlay](https://apis.io/overlays/klarna/klarna-merchantcard-overlay/)
- [Klarna Orders Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-orders-api-phrasing-overlay/)
- [Klarna Orders Overlay](https://apis.io/overlays/klarna/klarna-orders-overlay/)
- [Klarna Payments Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-payments-api-phrasing-overlay/)
- [Klarna Payments Overlay](https://apis.io/overlays/klarna/klarna-payments-overlay/)
- [Klarna Payouts Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-payouts-api-phrasing-overlay/)
- [Klarna Payouts Overlay](https://apis.io/overlays/klarna/klarna-payouts-overlay/)
- [Klarna Refunds Api Phrasing Overlay](https://apis.io/overlays/klarna/klarna-refunds-api-phrasing-overlay/)
- …and 5 more published on APIs.io

#### Governance rules (3)

Spectral rulesets for the provider's contracts.

- [Klarna — asyncapi rules](https://apis.io/rules/klarna/klarna-asyncapi-spectral-rules/)
- [Klarna — jsonschema rules](https://apis.io/rules/klarna/klarna-jsonschema-spectral-rules/)
- [Klarna API Rules](https://apis.io/rules/klarna/klarna-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Klarna Authentication](https://apis.io/security/klarna/klarna-authentication/)
- [Klarna Domain Security](https://apis.io/security/klarna/klarna-domain-security/)
- [Klarna Vulnerability Disclosure](https://apis.io/security/klarna/klarna-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Klarna Scopes](https://apis.io/scopes/klarna/klarna-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Klarna Plans Pricing](https://apis.io/plans/klarna/klarna-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Klarna Rate Limits](https://apis.io/rate-limits/klarna/klarna-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Klarna Finops](https://apis.io/finops/klarna/klarna-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.klarna.com/)
- [Documentation](https://docs.klarna.com/)
- [Getting started](https://docs.klarna.com/acquirer/klarna/resources/developer-tools/testing-payments/before-you-test/)
- [API reference](https://docs.klarna.com/api/kn/introduction/)
- [Pricing](https://x.klarnacdn.net/mepo/onboarding/pricing-annexes/pricing-annex-kp-CA-US-en-20230905.pdf)
- [Sign up](https://portal.playground.klarna.com/)
- [Support](https://www.klarna.com/us/help/)
- [Blog](https://www.klarna.com/international/press/category/blog/)
- [Security](https://www.klarna.com/international/responsible-disclosure/)
- [Terms of service](https://www.klarna.com/us/terms-of-use/)
- [Privacy policy](https://www.klarna.com/us/privacy-policy/)
- [GitHub](https://github.com/klarna)
- [Status](https://status.klarna.com/)

## API Evangelist rating

**Kin Score 73.6** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 66.9 |
| Contract governance | 35.6 |
| Operational transparency | 92.1 |
| Developer ergonomics | 73.2 |
| Access clarity | 59.2 |

**Agent readiness 46.0** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | verified |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 48.8** — Banking & Open Finance

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/klarna/](https://apis.io/providers/klarna/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Klarna: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/klarna/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
