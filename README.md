# Klarna (klarna)
Klarna Bank AB, commonly referred to as Klarna, is a Swedish fintech company
that provides online financial services. The company provides payment
processing services for the e-commerce industry, managing store claims and
customer payments. The company is a "buy now, pay later" service provider.

**URL:** [Visit APIs.json URL](
https://raw.githubusercontent.com/api-search/api-reference-introduction-klarna/refs/heads/main/apis.yml)

## Scope

- **Type:** Contract 
- **Position:** Consuming 
- **Access:** 3rd-Party 

## Tags:

 - Payments

## Timestamps

- **Created:** 2024-11-12 
- **Modified:** 2024-12-30 

## APIs

### Klarna Payments API V1

The payments API is used to create a session to offer Klarna's payment
methods as part of your checkout. As soon as the purchase is completed the
order should be read and handled using the [`Order Management
API`](https://docs.klarna.com/api/ordermanagement).

**Human URL:** [https://docs.klarna.com/api/payments/](https://docs.klarna.com/api/payments/)


#### Tags:

 - Payments

#### Properties

- [Documentation](https://docs.klarna.com/api/payments/)
- [OpenAPI](openapi/klarna-payments-api-openapi.yml)
### Klarna Payments API V1

The Customer Token API is used to charge customers with a tokenized Klarna
payment method and can be used for recurring purchases, subscriptions and
for storing a customer's payment method. Tokens are created using the
[`generate a customer token`](https://docs.klarna.com/api/payments/) call
in the payments API.

**Human URL:** [https://docs.klarna.com/api/customertoken/](https://docs.klarna.com/api/customertoken/)


#### Tags:

 - Customers, Tokens

#### Properties

- [Documentation](https://docs.klarna.com/api/customertoken/)
- [OpenAPI](openapi/klarna-customer-token-api-openapi.yml)
### Checkout API V3

The checkout API is used to create a checkout with Klarna and update the
checkout order during the purchase. As soon as the purchase is completed
the order should be read and handled using the [Order Management
API](https://docs.klarna.com/api/ordermanagement). Read more on [Klarna
checkout](https://docs.klarna.com/kco/).

**Human URL:** [https://docs.klarna.com/api/checkout/](https://docs.klarna.com/api/checkout/)


#### Tags:

 - Checkout

#### Properties

- [Documentation](https://docs.klarna.com/api/checkout/)
- [OpenAPI](openapi/kustom-checkout-api-openapi.yml)
### Checkout API V3

Klarna provides a number of different callbacks during the customer's
checkout session. The callbacks can be used to update the order when the
customer changes their address as well as to do a final check to validate
the order before it is submitted. The callbacks are sent as POST requests
to the endpoint you specify when creating the order. Your response is
interpreted using the response code and body. Read more on
[here](https://docs.klarna.com/kco/).

**Human URL:** [https://docs.klarna.com/api/checkout-merchant/](https://docs.klarna.com/api/checkout-merchant/)


#### Tags:

 - Checkout

#### Properties

- [Documentation](https://docs.klarna.com/api/checkout-merchant/)
- [OpenAPI](openapi/kustom-checkout-callback-api-openapi.yml)
### Hosted Payment Page (HPP)

Hosted Payment Page (HPP) API is a service that lets you integrate Klarna
Payments without the need of hosting the web page that manages the client
side of Klarna Payments.

**Human URL:** [https://docs.klarna.com/api/hpp-merchant/](https://docs.klarna.com/api/hpp-merchant/)


#### Tags:

 - Hosted, Payments, Pages

#### Properties

- [Documentation](https://docs.klarna.com/api/hpp-merchant/)
- [OpenAPI](openapi/hosted-payment-page-api-openapi.yml)
### Klarna Order Management API

The Order Management API is used for handling an order after the customer
has completed the purchase. It is used for all actions you need to manage
your orders. Examples being: updating, capturing, reading and refunding an
order.




Read more on the [Order
management](https://docs.klarna.com/order-management/) process.




# Authentication




<!-- ReDoc-Inject: <security-definitions> -->

**Human URL:** [https://docs.klarna.com/api/ordermanagement/](https://docs.klarna.com/api/ordermanagement/)


#### Tags:

 - Orders

#### Properties

- [Documentation](https://docs.klarna.com/api/ordermanagement/)
- [OpenAPI](openapi/order-management-api-openapi.yml)
### Merchant Card Service API

The Merchant Card Service (MCS) API is used to settle orders with virtual
credit cards.




Read more on [Merchant card
service](https://docs.klarna.com/merchant-card-service/).

**Human URL:** [https://docs.klarna.com/api/merchant-card-service/](https://docs.klarna.com/api/merchant-card-service/)


#### Tags:

 - Merchants, Cards

#### Properties

- [Documentation](https://docs.klarna.com/api/merchant-card-service/)
- [OpenAPI](openapi/merchant-card-service-api-openapi.yml)
### Shipping Service Callback API

The Integrator implements the Klarna Shipping Service Callback API as
described in the documentation. The Integrator is the upstream provider of
shipping options for KSS.

**Human URL:** [https://docs.klarna.com/api/merchant-shipping-introduction/](https://docs.klarna.com/api/merchant-shipping-introduction/)


#### Tags:

 - Shipping, Callbacks

#### Properties

- [Documentation](https://docs.klarna.com/api/merchant-shipping-introduction/)
### Klarna Settlements API

The Settlements API helps you with the reconciliation of payments, made by
Klarna to your bank account. Every payment has a unique payment_reference
that can be found in the settlement reports and on your bank statement.




Read more on [Settlement
reports](https://docs.klarna.com/settlement-reports/).




# Authentication




<!-- ReDoc-Inject: <security-definitions> -->

**Human URL:** [https://docs.klarna.com/api/settlements/](https://docs.klarna.com/api/settlements/)


#### Tags:

 - Settlements

#### Properties

- [Documentation](https://docs.klarna.com/api/settlements/)
- [OpenAPI](openapi/klarna-settlements-api-openapi.yml)
### Disputes API v2

The Disputes API offers Klarna partners and merchants an easy way to
handle customer disputes. 

**Human URL:** [https://docs.klarna.com/api/disputes-api/disputes-api_2.0.0/](https://docs.klarna.com/api/disputes-api/disputes-api_2.0.0/)


#### Tags:

 - Disputes, Payments

#### Properties

- [Documentation](https://docs.klarna.com/api/disputes-api/disputes-api_2.0.0/)
- [OpenAPI](openapi/klarna-disputes-api-openapi.yml)

## Common Properties

- [Authentication](https://docs.klarna.com/api/authentication/)
- [Errors](https://docs.klarna.com/api/errors/)
- [RateLimits](https://docs.klarna.com/api/rate-limit/)
- [Documentation](https://docs.klarna.com/)
- [Errors](
https://docs.klarna.com/resources/developer-tools/error-handling/error-codes-and-messages/)
- [Glossary](https://docs.klarna.com/resources/business-tools/glossary/)
- [Integrations](https://docs.klarna.com/platform-solutions/)
- [TermsOfService](
https://www.klarna.com/international/terms-and-conditions/?_gl=1*1842tzc*_ga*NDI0ODM2NTg2LjE3MzE0NTIyMDk.*_ga_F4RYPWHEGX*MTczMjU2NzcwMy4zLjEuMTczMjU2ODQyMS4wLjAuMjE4NDI5NzU5)
- [Status](https://status.klarna.com/)
- [StatusHistory](https://status.klarna.com/history)

## Maintainers

**FN:** Kin Lane

**Email:** info@apievangelist.com

