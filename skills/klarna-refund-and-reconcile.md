---
name: Refund a Klarna order and reconcile it to a payout
description: >-
  Refund a captured Klarna order, then trace the money through the Settlements API to the payout
  that carries it. The refund and reconciliation halves belong in one skill because Klarna keys
  them together on order_id and capture_id.
api: openapi/klarna-refunds-api-openapi.yml
operations:
  - refundOrder
  - get
  - cancelOrder
  - getTransactions
  - getPayouts
  - getPayout
  - getPayoutSummary
generated: '2026-08-27'
method: generated
source: openapi/klarna-refunds-api-openapi.yml, openapi/klarna-payouts-api-openapi.yml, openapi/klarna-transactions-api-openapi.yml
---

# Refund a Klarna order and reconcile it to a payout

## Choose the right reversal

- The order has **no captures** → `cancelOrder`,
  `POST /ordermanagement/v1/orders/{order_id}/cancel` (`204`).
- The order **has captures** → `refundOrder`. Klarna returns
  `403 CANCEL_NOT_ALLOWED` — "Order has previous captures. Cancel not possible" — if you try to
  cancel a captured order, and `403 REFUND_NOT_ALLOWED` — "Order has no captures. Refund not
  possible" — if you try to refund an uncaptured one. The two are mutually exclusive.

Klarna publishes **no calendar deadline** for refunds. The only stated constraint is that a
capture must exist and `refunded_amount` must be ≤ `captured_amount`.

## Refund

`refundOrder`, `POST /ordermanagement/v1/orders/{order_id}/refunds` → `201`.

- `refunded_amount` (required) — in minor units, ≤ the captured amount.
- `reference` (optional) — carried into the settlement files. **Set it.** It is the cheapest way
  to make step 3 below possible.
- `description` (optional) — shown to the shopper.
- `order_lines` (optional but recommended) — lets Klarna allocate the refund to the correct
  capture, i.e. the correct consumer invoice, and shows the shopper what was refunded in the
  Klarna app.
- Header: `Klarna-Idempotency-Key`. Klarna's own refund guide states retries are safe on network,
  socket and timeout errors when the key is present.

Read it back with `get`, `GET /ordermanagement/v1/orders/{order_id}/refunds/{refund_id}`.

## Reconcile

1. `getTransactions`, `GET /transactions` — the join table. Each row carries `order_id`,
   `short_order_id`, `capture_id`, `refund_id` and `payment_reference` at once, which is what
   makes the trace possible. Paginate with `offset` / `size`; read `pagination.total`.
2. `getPayout`, `GET /payouts/{payment_reference}` — the payout that settled those transactions.
3. `getPayouts` / `getPayoutSummary` for date-range views. `start_date` and `end_date` are
   required ISO 8601 date-times; Klarna recommends the full `2020-01-23T00:00:00Z` form rather
   than a bare date.

Note the base path: Settlements lives at `https://api.klarna.com/settlements/v1`, not at the bare
API root like Payments and Order Management.
