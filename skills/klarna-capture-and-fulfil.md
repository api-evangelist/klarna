---
name: Capture a Klarna order and attach fulfilment
description: >-
  Capture all or part of an authorized Klarna order when goods ship, attach tracking, and release
  the amount you will not use. This is the money-taking step — it is what makes the shopper owe
  Klarna and Klarna owe you.
api: openapi/klarna-captures-api-openapi.yml
operations:
  - captureOrder
  - getCaptures
  - getCapture
  - appendShippingInfo
  - appendOrderShippingInfo
  - triggerSendOut
  - releaseRemainingAuthorization
  - extendAuthorizationTime
generated: '2026-08-27'
method: generated
source: openapi/klarna-captures-api-openapi.yml, openapi/klarna-orders-api-openapi.yml
---

# Capture a Klarna order and attach fulfilment

## Rule

Capture when you ship, not when you sell. Klarna's capture is the event that creates the consumer
invoice.

## Steps

1. **Capture** — `captureOrder`, `POST /ordermanagement/v1/orders/{order_id}/captures`.
   Send `captured_amount` and, strongly recommended, `order_lines[]` so the consumer invoice shows
   the right items. Returns `201` with a `Location` header naming the new capture.
   Partial captures are allowed and repeatable — ship in three parcels, capture three times.

2. **Attach tracking** — `appendShippingInfo`,
   `POST /ordermanagement/v1/orders/{order_id}/captures/{capture_id}/shipping-info` (`204`),
   or `appendOrderShippingInfo` at order level. Append-only: there is no delete.

3. **Trigger the invoice send-out** — `triggerSendOut`,
   `POST /ordermanagement/v1/orders/{order_id}/captures/{capture_id}/trigger-send-out` (`204`).

4. **Release what you will not ship** — `releaseRemainingAuthorization`,
   `POST /ordermanagement/v1/orders/{order_id}/release-remaining-authorization` (`204`).
   Do this as soon as the final parcel is captured; leaving an authorization open holds the
   shopper's credit line.

5. **Need more time before capturing?** — `extendAuthorizationTime`,
   `POST /ordermanagement/v1/orders/{order_id}/extend-authorization-time` (`204`).

6. **Read back** — `getCaptures` (all) or `getCapture` (one).

## Error rules

- `403 CAPTURE_NOT_ALLOWED` — the order is cancelled or expired, or `captured_amount` exceeds the
  remaining authorized amount. Read the order with `getOrder` before deciding what to do.
- `403 NOT_ALLOWED` on `updateAuthorization` — you cannot reduce the authorization below the
  amount already captured.
- `404 NO_SUCH_ORDER` / `404 NO_SUCH_CAPTURE` — check the identifier.
- `413 REQUEST_TOO_LARGE` — the default body limit is 1MB; split large `order_lines[]`.

## Idempotency

Every capture MUST carry `Klarna-Idempotency-Key`. A capture without one, retried after a
timeout, can take the shopper's money twice. Klarna's own timeout guidance (`500` /
`error_code: TIMEOUT`, 59-second idle limit) assumes the key is present.
