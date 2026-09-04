---
name: Authorize a Klarna payment and create the order
description: >-
  Take a shopper basket from a Klarna payment session through browser authorization to a created
  order, using the Klarna Payments API. This is the entry point for every Klarna web checkout.
api: openapi/klarna-payments-api-openapi.yml
operations:
  - createCreditSession
  - updateCreditSession
  - readCreditSession
  - createOrder
  - cancelAuthorization
generated: '2026-08-27'
method: generated
source: openapi/klarna-payments-api-openapi.yml + conventions/klarna-conventions.yml
---

# Authorize a Klarna payment and create the order

## Before you start

- Base URL by region: `https://api.klarna.com/` (Europe), `https://api-na.klarna.com/`
  (North America), `https://api-oc.klarna.com/` (Oceania). Playground swaps in
  `api.playground.klarna.com` and friends. A `klarna_test_api_*` key **only** works against
  playground.
- Auth on every call: `Authorization: Basic <API key>`.
- Put `Klarna-Idempotency-Key: <UUID>` on every POST and PATCH. Klarna honours it for 24 hours
  and replays the original result on a duplicate.

## Steps

1. **Create the session** — `createCreditSession`, `POST /payments/v1/sessions`.
   Send `purchase_country`, `purchase_currency`, `locale`, `order_amount`, `order_tax_amount`
   and `order_lines[]`. Klarna validates that the order-line tax amounts sum to `order_tax_amount`
   and rejects mismatches with `400 BAD_VALUE : order_lines[X].total_tax_amount`.
   Keep the returned `session_id` and `client_token`.

2. **Render the widget** — hand `client_token` to the browser library
   `https://x.klarnacdn.net/kp/lib/v1/api.js`. The shopper completes the flow and the library
   returns an `authorization_token`. That token is valid for 60 minutes and can be consumed once.

3. **If the basket changes before authorization** — `updateCreditSession`,
   `POST /payments/v1/sessions/{session_id}`. Returns `204`. A `404 NOT_FOUND` with
   "Invalid session id" means the session expired: create a new one rather than retrying.

4. **Create the order** — `createOrder`,
   `POST /payments/v1/authorizations/{authorizationToken}/order`.
   The body must match what was authorized. A `409 BAD_VALUE` ("Not matching fields...") means
   the basket changed after authorization — start again at step 1.
   Keep the returned `order_id`; it is the key for everything after this point.

5. **If you will not use the authorization** — `cancelAuthorization`,
   `DELETE /payments/v1/authorizations/{authorizationToken}`. Returns `204`. Do this promptly;
   Klarna warns that cancelling can affect its credit assessment for the shopper's next attempt.

## Error rules

- `403 REJECTED` — Klarna declined the shopper. There is no reason code; offer another payment
  method. Do not retry.
- `403 MERCHANT_INACTIVE` — the MID is not live. This is a contract problem, not a code problem.
- `404 SESSION_COMPLETED` — an order already exists for this session. Read it, do not re-create.
- Retry `500` and `503` with the same `Klarna-Idempotency-Key`, exponential back-off, jitter.
- On `429`, read `X-Ratelimit-Remaining` and `X-Ratelimit-Reset` (always `1` for per-second
  limits) before retrying. There is no `Retry-After`.

## Reversibility

Before creating the order: `cancelAuthorization` clears it completely.
After creating the order: `cancelOrder` works only while the order has **no** captures.
See `conventions/klarna-conventions.yml`.
