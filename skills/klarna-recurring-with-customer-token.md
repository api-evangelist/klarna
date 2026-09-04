---
name: Set up recurring Klarna purchases with a customer token
description: >-
  Turn a one-time Klarna authorization into a reusable customer token, charge it for
  subscription or on-demand purchases, and cancel it cleanly. The only Klarna path that lets a
  merchant — or an agent acting for one — initiate a purchase without the shopper present.
api: openapi/klarna-customer-token-api-openapi.yml
operations:
  - purchaseToken
  - readCustomerToken
  - createOrder
  - patchCustomerToken
generated: '2026-08-27'
method: generated
source: openapi/klarna-customer-token-api-openapi.yml, openapi/klarna-payments-api-openapi.yml
---

# Recurring Klarna purchases with a customer token

## What a token is

A customer token persists a shopper's payment authorization so you can charge it later without
the shopper being present. It is the highest-consequence object in the Klarna merchant surface:
holding one means you can move the shopper's money on your own initiative.

## Steps

1. **Get the shopper's consent and an authorization** — run the standard payment session and
   browser `authorize()` flow with the recurring intent set. See
   `klarna-authorize-and-create-order.md`.

2. **Exchange the authorization for a token** — `purchaseToken`,
   `POST /payments/v1/authorizations/{authorizationToken}/customer-token` → `200`.
   Keep the returned token. A `403 INVALID_OPERATION` with "Not allowed to create customer token
   for intent buy" means the payment method the shopper picked does not support tokenization —
   not every one does.

3. **Check the token before charging it** — `readCustomerToken`,
   `GET /customer-token/v1/tokens/{customerToken}` → `200`. Returns the token status and the
   payment method behind it (card or direct debit). Do this before any charge an agent initiates;
   a stale token produces a failed charge and a confused shopper.

4. **Charge it** — `createOrder`,
   `POST /customer-token/v1/tokens/{customerToken}/order` → `200`.
   Send `order_lines[]`, amounts and `merchant_urls` as for a normal order. `Klarna-Idempotency-Key`
   is mandatory here: a duplicated subscription charge is the worst failure mode on this surface.

5. **Cancel the token** — `patchCustomerToken`,
   `PATCH /customer-token/v1/tokens/{customerToken}/status` → `202`.
   Asynchronous. Do this the moment the shopper cancels the subscription — Klarna publishes no
   automatic expiry for tokens.

## Error rules

- `403` on the charge — the token was cancelled or the MID is not configured for recurring.
- `409` — a duplicate order under a different body. Read before you retry.
- `404` — the token does not exist or was deleted.

## Agent guidance

Every operation in step 4 is classified `acting` / `physical` in
`agentic-access/klarna-agentic-access.yml` with a 300-second token TTL ceiling and
`purpose-required` escalation. Treat a customer-token charge as a human-confirmable action unless
the merchant has explicitly delegated recurring billing.
