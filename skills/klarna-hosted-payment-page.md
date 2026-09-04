---
name: Sell without a checkout page using the Klarna Hosted Payment Page
description: >-
  Create a Klarna-hosted payment page, have Klarna deliver the link to the shopper by email or
  SMS, and follow the session to a completed order. The right skill when there is no merchant
  checkout to embed a widget into — phone orders, invoices, in-store, agent-initiated purchases.
api: openapi/klarna-hpp-api-openapi.yml
operations:
  - createHppSession
  - getSessionById
  - distributeHppSession
  - disableHppSession
  - createCreditSession
generated: '2026-08-27'
method: generated
source: openapi/klarna-hpp-api-openapi.yml
---

# Sell with the Klarna Hosted Payment Page

## Why this path

HPP needs no client-side library and no merchant checkout page. Klarna hosts the whole purchase
surface; you hold a `session_id` and a URL.

## Steps

1. **Create the underlying payment session** — `createCreditSession`,
   `POST /payments/v1/sessions`. Keep the `session_id`.

2. **Create the HPP session** — `createHppSession`, `POST /hpp/v1/sessions` → `201`.
   Reference the payment session, and supply `merchant_urls` for `success`, `cancel`, `back`,
   `failure` and `status_update`. The response carries the hosted URL to send the shopper to,
   plus the HPP `session_id`.

3. **Let Klarna deliver it** — `distributeHppSession`,
   `POST /hpp/v1/sessions/{session_id}/distribution` → `201`/`204`. Klarna sends the link to the
   shopper by email or SMS from the contact details in the request. A `503` here is retryable
   with the same `Klarna-Idempotency-Key`.

4. **Follow the session** — `getSessionById`, `GET /hpp/v1/sessions/{session_id}`. Klarna also
   pushes status callbacks to your `status_update` URL; see
   `asyncapi/klarna-push-notifications-asyncapi.yml`.

5. **Kill it if the deal falls through** — `disableHppSession`,
   `DELETE /hpp/v1/sessions/{session_id}` → `204`. Do this rather than leaving a live payment
   link outstanding.

## Error rules

- `401` — wrong or missing API key, or a test key against a live host.
- `403` — the operation is not enabled for this MID; HPP is a contracted product.
- `404` — the session expired or the id is wrong.
- `503` on distribution — Klarna's delivery channel is temporarily unavailable. Retry with the
  same idempotency key; do not create a second session.
