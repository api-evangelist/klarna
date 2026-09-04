# Klarna GraphQL Schema

> **NOT PUBLISHED BY KLARNA.** Verified 2026-08-27: Klarna ships no GraphQL API. There is no
> `/graphql` endpoint on api.klarna.com, no GraphQL surface in Klarna's 79 KB `llms.txt`, and no
> mention of GraphQL anywhere in docs.klarna.com. Every Klarna merchant API is REST/JSON.
> This document and `klarna-schema.graphql` are a **conceptual re-modelling** authored by API
> Evangelist, not a Klarna artifact. They are retained as a design exercise only. The
> `type: GraphQL` pointer that previously advertised them in `apis.yml` has been REMOVED, because
> it asserted on Klarna's behalf that Klarna publishes a GraphQL contract, which Klarna does not.


This document describes a conceptual GraphQL schema for the Klarna payments and BNPL (Buy Now, Pay Later) platform. The schema covers the full merchant integration surface: payment sessions, authorizations, order management, customer tokens, settlements, disputes, and webhooks.

## Overview

Klarna provides a suite of APIs enabling merchants to offer flexible payment options including Pay-in-3, Pay-in-30, and financing plans. This GraphQL schema unifies those REST endpoints into a single typed graph.

## Schema Source

- **Provider**: Klarna
- **Documentation**: https://docs.klarna.com/
- **Base URL**: https://api.klarna.com
- **Schema File**: klarna-schema.graphql

## Type Summary

### Session Types
- `Session` — A Klarna payment session created to initialize the client-side widget.
- `SessionDetails` — Extended metadata for a session including locale, currency, and merchant reference.
- `SessionStatus` — Enum representing the lifecycle state of a session (INCOMPLETE, COMPLETE, DISABLED).

### Authorization Types
- `Authorization` — A customer authorization captured after the Klarna widget flow completes.
- `AuthorizationDetails` — Full authorization payload including fraud status and expiry.

### Order Types
- `Order` — A Klarna order created against an authorization.
- `OrderDetails` — Full order payload with line items, addresses, and amounts.
- `OrderStatus` — Enum for order lifecycle (AUTHORIZED, PART_CAPTURED, CAPTURED, CANCELLED, EXPIRED, CLOSED).

### Capture Types
- `Capture` — A full or partial capture of an authorized order.
- `CaptureDetails` — Amount, shipping info, and line items for a capture.

### Refund Types
- `Refund` — A refund against a captured order.
- `RefundDetails` — Amount, description, and line items for a refund.

### Customer Types
- `Customer` — A Klarna customer identity associated with a session or token.
- `CustomerDetails` — PII fields: name, email, phone, date of birth.
- `CustomerToken` — A persistent tokenized payment method for recurring purchases.

### Address Types
- `BillingAddress` — The billing address for a payment session or order.
- `ShippingAddress` — The delivery address for physical or digital goods.

### Line Item Types
- `LineItem` — A single product or service in a cart.
- `LineItemDetails` — SKU, product URL, image URL, category, and tax rate.
- `ItemType` — Enum for line item categorization (PHYSICAL, DIGITAL, SHIPPING_FEE, SALES_TAX, DISCOUNT, STORE_CREDIT, GIFT_CARD, SURCHARGE).

### Image and URL Types
- `ImageURL` — A structured URL reference for a product image.

### Shipping Types
- `Shipping` — Shipping selection attached to a capture.
- `ShippingDetails` — Carrier, tracking number, and service level.
- `Carrier` — The shipping carrier (e.g., UPS, USPS, FedEx, DHL).
- `TrackingNumber` — A carrier-issued tracking reference.

### Discount Types
- `Discount` — A discount applied to the cart.
- `DiscountDetails` — Amount, description, and promotion code linkage.
- `PromotionCode` — A merchant-issued promotion or coupon code.

### Payment Method Types
- `PaymentMethod` — A payment method offered to the customer.
- `PaymentMethodType` — Enum for method category (INVOICE, DIRECT_DEBIT, DIRECT_BANK_TRANSFER, CARD, PAYLATER, SLICE_IT, SLICE_IT_BY_CARD, PAY_NOW, PAY_OVER_TIME).

### Financing Types
- `FinancingOption` — A financing offer presented to the customer.
- `InstallmentDetails` — Number of installments, monthly amount, and total amount.
- `Plan` — A payment plan identifier.
- `PaymentPlan` — A specific repayment schedule for financing.
- `InterestRate` — The annual percentage rate (APR) for a financing plan.

### Merchant Types
- `Merchant` — The merchant entity associated with a transaction.
- `MerchantDetails` — Name, country, and terms/privacy URLs.
- `MerchantReference` — A merchant-supplied order or session reference pair.

### Payout and Settlement Types
- `Payout` — A Klarna payout disbursed to the merchant bank account.
- `PayoutDetails` — Amount, currency, and reference for a payout.
- `Settlement` — A settlement record grouping transactions in a reporting period.
- `SettlementDetails` — Statement period, transactions, and net amounts.
- `SettlementType` — Enum for settlement classification (INVOICE, CREDIT_NOTE, CORRECTION).

### Dispute and Chargeback Types
- `Dispute` — A customer dispute raised against an order.
- `DisputeDetails` — Reason, evidence deadline, and resolution details.
- `DisputeStatus` — Enum for dispute state (OPEN, PENDING_EVIDENCE, RESOLVED, LOST, WON).
- `Chargeback` — A payment reversal issued by the card network.
- `ChargebackDetails` — Amount, reason code, and associated order reference.

### Webhook Types
- `Webhook` — A registered merchant webhook endpoint.
- `WebhookEvent` — An outbound event payload sent to the merchant callback URL.

### Auth Types
- `APIKey` — A Klarna API credential used for server-to-server requests.
- `Token` — A short-lived bearer token or session token.

## Query Examples

```graphql
query GetSession($sessionId: ID!) {
  session(id: $sessionId) {
    sessionId
    status
    paymentMethodCategories {
      identifier
      name
      assetUrls {
        descriptive
        standard
      }
    }
  }
}

query GetOrder($orderId: ID!) {
  order(id: $orderId) {
    orderId
    status
    orderAmount
    capturedAmount
    remainingAuthorizedAmount
    lineItems {
      name
      quantity
      unitPrice
      totalAmount
    }
  }
}

query ListSettlements($merchantId: ID!, $startDate: String!, $endDate: String!) {
  settlements(merchantId: $merchantId, startDate: $startDate, endDate: $endDate) {
    settlementId
    settlementType
    totalAmount
    currency
    payoutDate
  }
}
```

## Mutation Examples

```graphql
mutation CreateSession($input: CreateSessionInput!) {
  createSession(input: $input) {
    sessionId
    clientToken
    paymentMethodCategories {
      identifier
      name
    }
  }
}

mutation AuthorizeOrder($sessionId: ID!, $input: AuthorizationInput!) {
  authorizeOrder(sessionId: $sessionId, input: $input) {
    authorizationToken
    approved
    fraudStatus
  }
}

mutation CaptureOrder($orderId: ID!, $input: CaptureInput!) {
  captureOrder(orderId: $orderId, input: $input) {
    captureId
    capturedAmount
    capturedAt
  }
}

mutation RefundCapture($orderId: ID!, $captureId: ID!, $input: RefundInput!) {
  refundCapture(orderId: $orderId, captureId: $captureId, input: $input) {
    refundId
    refundedAmount
    description
  }
}

mutation CreateCustomerToken($authorizationToken: String!, $input: CustomerTokenInput!) {
  createCustomerToken(authorizationToken: $authorizationToken, input: $input) {
    tokenId
    status
    paymentMethodType
  }
}
```
