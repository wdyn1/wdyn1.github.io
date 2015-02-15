# Resources
## Connections

Establishes a connection to the Zuora REST API service based on a valid user credentials.

This call authenticates the user and returns an API session cookie that's used to authorize subsequent calls to the REST API. A call to connections is a required first step before using the Zuora REST API to access data.

The credentials must belong to a user account that has permission to access the API service.

> Replace `$USER_NAME` with your user name and `$PASSWORD` with your password 

```shell
curl -i -k -H "apiAccessKeyId:$USER_NAME" -H "apiSecretAccessKey:$PASSWORD" -H "Accept:application/json" -X POST $BASE_URL/connections
```

> Response

```json
{
  "success": true,
}
```

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/connections`

### Request Parameters
|Parameter| |Description 
---------|--------|-----------
**apiAccessKeyId**|required|Account username
**apiSecretAccessKey**|required|Account password
**Content-Type**|required|Must be set to "application/json"


## Accounts

The Accounts REST API provides direct access to customer account information.

## HTTP Request1

> Replace `$USER_NAME` with your user name and `$PASSWORD` with your password 

```shell
curl -i -k -H "apiAccessKeyId:$USER_NAME" -H "apiSecretAccessKey:$PASSWORD" -H "Content-Type:application/json" -H "Accept:application/json" -d
```
> Request Body

```json
{
    "name": "CRestTestingAccount",
    "currency": "USD",
    "notes": "this account is for crest account creation demo",
    "billCycleDay": 1,
    "paymentTerm": "Due Upon Receipt",
    "billToContact": {
        "address1": "3400 Bridge Pkwy",
        "address2": "#000",
        "city": "Redwood City",
        "country": "United States",
        "county": "San Mateo",
        "fax": "+1(123)4567890",
        "firstName": "Leo",
        "homePhone": "+1(123)4567890",
        "lastName": "Liu",
        "mobilePhone": "+1(123)4567890",
        "nickname": "LW",
        "otherPhone": "+1(123)4567890",
        "otherPhoneType": "Other",
        "personalEmail": "leo@test.com",
        "zipCode": "94000",
        "state": "CA",
        "taxRegion": "CA",
        "workEmail": "leo@test.com",
        "workPhone": "+1(123)4567890"
    },
    "soldToContact": {
        "address1": "3400 Bridge Pkwy",
        "address2": "#000",
        "city": "Redwood City",
        "country": "United States",
        "county": "San Mateo",
        "fax": "+1(123)4567890",
        "firstName": "J",
        "homePhone": "+1(123)4567890",
        "lastName": "C",
        "mobilePhone": "+1(123)4567890",
        "nickname": "J",
        "otherPhone": "+1(123)4567890",
        "otherPhoneType": "Other",
        "personalEmail": "j.c@test.com",
        "zipCode": "94000",
        "state": "CA",
        "taxRegion": "CA",
        "workEmail": "j.c@test.com",
        "workPhone": "+1(123)4567890"
    },
    "creditCard": {
        "cardType": "Visa",
        "cardNumber": "4111111111111111",
        "expirationMonth": 12,
        "expirationYear": 2020,
        "securityCode": null,
        "cardHolderInfo": {
            "cardHolderName": "Leo",
            "addressLine1": "3400 Bridge Pkwy",
            "addressLine2": "#000",
            "city": null,
            "state": null,
            "zipCode": "94000",
            "country": "United States",
            "phone": "+1(123)4567890",
            "email": "w.l@test.com"
        }
    }
}
```

> Response

```json
{
  "paymentMethodId": "2c92c8f83dcbd8b1013dcce096b0000b",
  "paymentId": "2c92c8f83dcbd8b1013dcce09f420032",
  "paidAmount": 599.55,
  "subscriptionNumber": "A-S00001083",
  "subscriptionId": "2c92c8f83dcbd8b1013dcce0983b0015",
  "accountId": "2c92c8f83dcbd8b1013dcce096790008",
  "success": true,
  "accountNumber": "A00030968",
  "invoiceId": "2c92c8f83dcbd8b1013dcce09d110025"
}
```

`POST https://api-sandbox.zuora.com/rest/v1/accounts`

This REST API reference describes how to create a customer account with a credit-card payment method, a bill-to contact, and an optional sold-to contact. Request and response field descriptions and sample code are provided. Use this call to optionally create a subscription, invoice for that subscription, and collect payment through the default payment method. The transaction is atomic; if any part fails for any reason, the entire transaction is rolled back.

## HTTP Request2

> Request

```shell
curl -i -k -H "apiAccessKeyId:$USER_NAME" -H "apiSecretAccessKey:$PASSWORD" -H "Accept:application/json" -X GET $BASE_URL/v1/accounts/A00000001
```

> Response

```json
{
  "metrics": {
    "totalInvoiceBalance": 0.0,
    "contractedMrr": 15983.17,
    "creditBalance": 0.0,
    "balance": 0.0
  },
  "basicInfo": {
    "communicationProfileId": "c4ebdd8098bc102dac4f001517641b94",
    "status": "Active",
    "invoiceTemplateId": null,
    "crmId": "",
    "name": "subscribeCallYan_1",
    "notes": "",
    "accountNumber": "A00001115",
    "id": "2c92a0f9391832b10139183e277a0042",
    "dfadsf__c": null
  },
  "soldToContact": {
    "zipCode": "95135",
    "taxRegion": "",
    "fax": "",
    "country": "United States",
    "county": "",
    "personalEmail": "personal_email@zbcloud.com",
    "nickname": "",
    "otherPhone": "",
    "otherPhoneType": "Work",
    "lastName": "Zou",
    "workEmail": "work_email@zbcloud.com",
    "homePhone": "",
    "state": "California",
    "firstName": "Cheng",
    "address2": "",
    "address1": "1400 Bridge Pkwy",
    "workPhone": "5555551212",
    "city": "San Jose",
    "mobilePhone": ""
  },
  "success": true,
  "billToContact": {
    "zipCode": "95135",
    "taxRegion": "",
    "fax": "",
    "country": "United States",
    "county": "",
    "personalEmail": "personal_email@zbcloud.com",
    "nickname": "",
    "otherPhone": "",
    "otherPhoneType": "Work",
    "lastName": "Zou",
    "workEmail": "work_email@zbcloud.com",
    "homePhone": "",
    "state": "California",
    "firstName": "Cheng",
    "address2": "",
    "address1": "1400 Bridge Pkwy",
    "workPhone": "5555551212",
    "city": "San Jose",
    "mobilePhone": ""
  },
  "billingAndPayment": {
    "billCycleDay": 1,
    "paymentTerm": "Due Upon Receipt",
    "currency": "USD"
  }
  "batch": "Australia"
}
```

`PUT https://api-sandbox.zuora.com/rest/v1/accounts/{account-key:.*}`

This REST API reference describes how to retrieve basic information about a customer account.

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/accounts/{account-key:.*}/summary`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/accounts/{account-key:.*}`

## Catalog

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/catalog/products`

## Charge-Revenue-Summaries

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/charge-revenue-summaries/{rs-key}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/charge-revenue-summaries/subscription-charges/{charge-key}`

## Files

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/files/{file-id}`

## Hostedpages

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/hostedpages/{page-id:.*}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/hostedpages`

## Jom

### HTTP Request
`DELETE https://api-sandbox.zuora.com/rest/v1/jom/**`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/jom`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/jom/**`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/jom/**`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/jom/**`

## Operations

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/operations/template-validation`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/operations/document-generation`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/operations/invoice-collect`

## Payment-Methods

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/payment-methods/credit-cards`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/payment-methods/credit-cards/{payment-method-id}`

### HTTP Request
`DELETE https://api-sandbox.zuora.com/rest/v1/payment-methods/{payment-method-id}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/payment-methods/credit-cards/accounts/{account-key:.*}`

## Quotes

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/quotes/document`

## Rsa-Signatures

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/rsa-signatures`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/rsa-signatures/decrypt`

## Revenue-Events

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-events/{rs-key}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-events/revenue-schedules/{rs-key}`

## Revenue-Items

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-items/charge-revenue-summaries/{rs-key}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-items/revenue-schedules/{rs-key}`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/revenue-items/revenue-schedules/{rs-key}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-items/revenue-events/{rs-key}`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/revenue-items/revenue-events/{rs-key}`

## Revenue-Recognition-Rules

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-recognition-rules/subscription-charges/{charge-key}`

## Revenue-Schedules

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/revenue-schedules/{rs-key}/distribute-revenue-with-date-range`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/revenue-schedules/{rs-key}/distribute-revenue-across-accounting-periods`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/revenue-schedules/{rs-key}/basic-information`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-schedules/{rs-key}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-schedules/invoice-items/{ii-id}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-schedules/invoice-item-adjustments/{iia-id}`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/revenue-schedules/subscription-charges/{charge-key}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/revenue-schedules/subscription-charges/{charge-key}`

## Hmac-Signatures

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/hmac-signatures`

## Subscriptions

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/subscriptions/{subscription-id:.*}`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/subscriptions/{subscription-id:.*}/cancel`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/subscriptions`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/subscriptions/accounts/{account-key:.*}`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/subscriptions/preview`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/subscriptions/{subscription-id:.*}`

### HTTP Request
`PUT https://api-sandbox.zuora.com/rest/v1/subscriptions/{subscription-id:.*}/renew`

## Tenant

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/tenant/account-number/{tenant-id:.*}`

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/tenant`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/tenant/info`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/tenant/info/{tenant-id:.*}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/tenant/sandboxes`

## Transactions

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/transactions/payments/accounts/{account-key:.*}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/transactions/invoices/accounts/{account-key:.*}`

## Usage

### HTTP Request
`POST https://api-sandbox.zuora.com/rest/v1/usage`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/usage/accounts/{account-key:.*}`

### HTTP Request
`GET https://api-sandbox.zuora.com/rest/v1/usage/{importID}/status`

## Wadl

