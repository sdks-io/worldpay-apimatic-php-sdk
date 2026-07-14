# Authorizations

```php
$authorizationsApi = $client->getAuthorizationsApi();
```

## Class Name

`AuthorizationsApi`

## Methods

* [Get Authorizations Summary](../../doc/controllers/authorizations.md#get-authorizations-summary)
* [Get Authorizations Summary by Card Network](../../doc/controllers/authorizations.md#get-authorizations-summary-by-card-network)
* [Get Authorizations Summaryby Transaction Date](../../doc/controllers/authorizations.md#get-authorizations-summaryby-transaction-date)
* [Get Authorizations Summaryby Merchant](../../doc/controllers/authorizations.md#get-authorizations-summaryby-merchant)
* [Get Authorizations Summaryby Division](../../doc/controllers/authorizations.md#get-authorizations-summaryby-division)
* [Get Authorizations Summaryby Store](../../doc/controllers/authorizations.md#get-authorizations-summaryby-store)
* [Get Authorizations Summaryby Chain](../../doc/controllers/authorizations.md#get-authorizations-summaryby-chain)
* [Get Authorizations Summaryby Super Chain](../../doc/controllers/authorizations.md#get-authorizations-summaryby-super-chain)


# Get Authorizations Summary

Resource to get the total summary of authorizations for a given hierarchy and date range with card type and card network being optional parameters. Refer to the  schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummary(AuthTransactionsRequest $body, ?string $vCorrelationId = null): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`AuthTransactionsRequest`](../../doc/models/auth-transactions-request.md) | Body, Required | - |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SummaryResponses`](../../doc/models/summary-responses.md).

## Example Usage

```php
$body = AuthTransactionsRequestBuilder::init(
    EntityBuilder::init()
        ->level(Level::CHAIN)
        ->values(
            [
                'TSTC04',
                'TSTC14',
                'TSTC16'
            ]
        )
        ->build(),
    DateRangeBuilder::init(
        '2024-11-01',
        '2024-11-07'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummary($body);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SummaryResponses:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "totalApprovedCount": 11,
  "totalApprovedAmount": 965.02,
  "totalDeclinedCount": 22,
  "totalDeclinedAmount": 3092.19,
  "totalApprovedCountPercent": 33.33,
  "totalApprovedAmountPercent": 23.79,
  "totalDeclinedCountPercent": 66.67,
  "totalDeclinedAmountPercent": 76.21,
  "totalCount": 33,
  "totalAmount": 4057.21
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummary0ErrorException`](../../doc/models/authorizations-summary-0-error-exception.md) |


# Get Authorizations Summary by Card Network

Resource to get the summary of authorizations grouped by card networks for a given hierarchy and date range with card type and card network being optional parameters. Refer to the schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummaryByCardNetwork(
    ?string $vCorrelationId = null,
    ?AuthTransactionsSummaryRequestByCardNetwork $body = null
): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |
| `body` | [`?AuthTransactionsSummaryRequestByCardNetwork`](../../doc/models/auth-transactions-summary-request-by-card-network.md) | Body, Optional | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AuthorizationsSummaryCardnetworkResponse`](../../doc/models/authorizations-summary-cardnetwork-response.md).

## Example Usage

```php
$body = AuthTransactionsSummaryRequestByCardNetworkBuilder::init(
    EntityBuilder::init()
        ->level(Level::MERCHANT)
        ->values(
            [
                '2345045480016'
            ]
        )
        ->build(),
    DateRangeBuilder::init(
        '2024-10-11',
        '2024-11-09'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummaryByCardNetwork(
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AuthorizationsSummaryCardnetworkResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "pagination": {
    "pageNumber": 1,
    "pageSize": 25,
    "totalRowCount": 10,
    "totalReturnedCount": 10
  },
  "totalApprovedCount": 21,
  "totalApprovedAmount": 2895.12,
  "totalDeclinedCount": 45,
  "totalDeclinedAmount": 7527.6,
  "totalApprovedCountPercent": 31.82,
  "totalApprovedAmountPercent": 27.78,
  "totalDeclinedCountPercent": 68.18,
  "totalDeclinedAmountPercent": 72.22,
  "totalCount": 66,
  "totalAmount": 10422.72,
  "summaries": [
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "7",
        "shortDescription": "AMEX",
        "longDescription": "AMEX"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 9,
      "declinedAmount": 1737.36,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 100,
      "declinedAmountPercent": 100
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "L",
        "shortDescription": "BILL ME LATER",
        "longDescription": "BILL ME LATER"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "8",
        "shortDescription": "DINERS",
        "longDescription": "DINERS"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "6",
        "shortDescription": "DISCOVER",
        "longDescription": "DISCOVER"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 15,
      "declinedAmount": 2895.18,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 100,
      "declinedAmountPercent": 100
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "2",
        "shortDescription": "JCB",
        "longDescription": "JCB"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "1",
        "shortDescription": "MASTERCARD",
        "longDescription": "MASTERCARD"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 21,
      "declinedAmount": 2895.06,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 100,
      "declinedAmountPercent": 100
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "9",
        "shortDescription": "PRIVATE LABEL",
        "longDescription": "PRIVATE LABEL"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "4",
        "shortDescription": "VISA",
        "longDescription": "VISA"
      },
      "approvedCount": 21,
      "approvedAmount": 2895.12,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 100,
      "approvedAmountPercent": 100,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "V",
        "shortDescription": "VOYAGER",
        "longDescription": "VOYAGER"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0
    },
    {
      "cardType": "CREDIT",
      "cardNetwork": {
        "code": "W",
        "shortDescription": "WRIGHT EXPRESS",
        "longDescription": "WRIGHT EXPRESS"
      },
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummaryCardnetwork0ErrorException`](../../doc/models/authorizations-summary-cardnetwork-0-error-exception.md) |


# Get Authorizations Summaryby Transaction Date

Resource to get the summary of authorizations grouped by transaction dates for a given hierarchy and date range with card type and card network being optional parameters. Refer to the schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummarybyTransactionDate(
    ?string $vCorrelationId = null,
    ?AuthTransactionsSummaryRequestByTransactionDate $body = null
): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |
| `body` | [`?AuthTransactionsSummaryRequestByTransactionDate`](../../doc/models/auth-transactions-summary-request-by-transaction-date.md) | Body, Optional | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AuthorizationsSummaryTransactiondateResponse`](../../doc/models/authorizations-summary-transactiondate-response.md).

## Example Usage

```php
$body = AuthTransactionsSummaryRequestByTransactionDateBuilder::init(
    EntityBuilder::init()
        ->level(Level::MERCHANT)
        ->values(
            [
                '2345045480016'
            ]
        )
        ->build(),
    DateRangeBuilder::init(
        '2024-10-11',
        '2024-11-09'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummarybyTransactionDate(
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AuthorizationsSummaryTransactiondateResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "pagination": {
    "pageNumber": 1,
    "pageSize": 25,
    "totalRowCount": 3,
    "totalReturnedCount": 3
  },
  "totalApprovedCount": 21,
  "totalApprovedAmount": 2895.12,
  "totalDeclinedCount": 45,
  "totalDeclinedAmount": 7527.6,
  "totalApprovedCountPercent": 31.82,
  "totalApprovedAmountPercent": 27.78,
  "totalDeclinedCountPercent": 68.18,
  "totalDeclinedAmountPercent": 72.22,
  "totalCount": 66,
  "totalAmount": 10422.72,
  "summaries": [
    {
      "transactionDate": "2024-10-23",
      "approvedCount": 7,
      "approvedAmount": 965.04,
      "declinedCount": 15,
      "declinedAmount": 2509.2,
      "approvedCountPercent": 31.82,
      "approvedAmountPercent": 27.78,
      "declinedCountPercent": 68.18,
      "declinedAmountPercent": 72.22
    },
    {
      "transactionDate": "2024-10-24",
      "approvedCount": 7,
      "approvedAmount": 965.04,
      "declinedCount": 15,
      "declinedAmount": 2509.2,
      "approvedCountPercent": 31.82,
      "approvedAmountPercent": 27.78,
      "declinedCountPercent": 68.18,
      "declinedAmountPercent": 72.22
    },
    {
      "transactionDate": "2024-11-07",
      "approvedCount": 7,
      "approvedAmount": 965.04,
      "declinedCount": 15,
      "declinedAmount": 2509.2,
      "approvedCountPercent": 31.82,
      "approvedAmountPercent": 27.78,
      "declinedCountPercent": 68.18,
      "declinedAmountPercent": 72.22
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummaryTransactiondate0ErrorException`](../../doc/models/authorizations-summary-transactiondate-0-error-exception.md) |


# Get Authorizations Summaryby Merchant

Resource to get the summary of authorizations for given parameters grouped by merchants for a given hierarchy and date range with card type and card network being optional parameters. Refer to the schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummarybyMerchant(
    ?string $vCorrelationId = null,
    ?AuthTransactionsSummaryRequestByMerchant $body = null
): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |
| `body` | [`?AuthTransactionsSummaryRequestByMerchant`](../../doc/models/auth-transactions-summary-request-by-merchant.md) | Body, Optional | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SummaryDetailMerchant`](../../doc/models/summary-detail-merchant.md).

## Example Usage

```php
$body = AuthTransactionsSummaryRequestByMerchantBuilder::init(
    EntityBuilder::init()
        ->level(Level::MERCHANT)
        ->values(
            [
                '2345045480016'
            ]
        )
        ->build(),
    DateRangeBuilder::init(
        '2024-10-09',
        '2024-11-07'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummarybyMerchant(
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SummaryDetailMerchant:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "pagination": {
    "pageNumber": 1,
    "pageSize": 25,
    "totalRowCount": 1,
    "totalReturnedCount": 1
  },
  "totalApprovedCount": 21,
  "totalApprovedAmount": 2895.12,
  "totalDeclinedCount": 45,
  "totalDeclinedAmount": 7527.6,
  "totalApprovedCountPercent": 31.82,
  "totalApprovedAmountPercent": 27.78,
  "totalDeclinedCountPercent": 68.18,
  "totalDeclinedAmountPercent": 72.22,
  "totalCount": 66,
  "totalAmount": 10422.72,
  "summaries": [
    {
      "approvedCount": 21,
      "approvedAmount": 2895.12,
      "declinedCount": 45,
      "declinedAmount": 7527.6,
      "approvedCountPercent": 31.82,
      "approvedAmountPercent": 27.78,
      "declinedCountPercent": 68.18,
      "declinedAmountPercent": 72.22,
      "merchantId": "2345045480016"
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummaryMerchant0ErrorException`](../../doc/models/authorizations-summary-merchant-0-error-exception.md) |


# Get Authorizations Summaryby Division

Resource to get the summary of authorizations grouped by divisions for a given hierarchy and date range with card type and card network being optional parameters. Refer to the schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummarybyDivision(
    ?string $vCorrelationId = null,
    ?AuthTransactionsRequestByDivision $body = null
): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |
| `body` | [`?AuthTransactionsRequestByDivision`](../../doc/models/auth-transactions-request-by-division.md) | Body, Optional | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SummaryDetailDivision`](../../doc/models/summary-detail-division.md).

## Example Usage

```php
$body = AuthTransactionsRequestByDivisionBuilder::init(
    EntityBuilder::init()
        ->level(Level::CHAIN)
        ->values(
            [
                'TSTC04',
                'TSTC14',
                'TSTC16'
            ]
        )
        ->build(),
    DateRangeBuilder::init(
        '2024-10-09',
        '2024-11-07'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummarybyDivision(
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SummaryDetailDivision:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummaryDivision0ErrorException`](../../doc/models/authorizations-summary-division-0-error-exception.md) |


# Get Authorizations Summaryby Store

Resource to get the summary of authorizations grouped by stores for a given hierarchy and date range with card type and card network being optional parameters. Refer to the schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummarybyStore(
    ?string $vCorrelationId = null,
    ?AuthTransactionsRequestByStore $body = null
): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |
| `body` | [`?AuthTransactionsRequestByStore`](../../doc/models/auth-transactions-request-by-store.md) | Body, Optional | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SummaryDetailStore`](../../doc/models/summary-detail-store.md).

## Example Usage

```php
$body = AuthTransactionsRequestByStoreBuilder::init(
    EntityBuilder::init()
        ->level(Level::STORE)
        ->values(
            [
                '000000001'
            ]
        )
        ->chainCode('TSTC04')
        ->build(),
    DateRangeBuilder::init(
        '2024-10-11',
        '2024-11-09'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummarybyStore(
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SummaryDetailStore:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "pagination": {
    "pageNumber": 1,
    "pageSize": 25,
    "totalRowCount": 1,
    "totalReturnedCount": 1
  },
  "totalApprovedCount": 24,
  "totalApprovedAmount": 3477.15,
  "totalDeclinedCount": 54,
  "totalDeclinedAmount": 9273.69,
  "totalApprovedCountPercent": 30.77,
  "totalApprovedAmountPercent": 27.27,
  "totalDeclinedCountPercent": 69.23,
  "totalDeclinedAmountPercent": 72.73,
  "totalCount": 78,
  "totalAmount": 12750.84,
  "summaries": [
    {
      "approvedCount": 24,
      "approvedAmount": 3477.15,
      "declinedCount": 54,
      "declinedAmount": 9273.69,
      "approvedCountPercent": 30.77,
      "approvedAmountPercent": 27.27,
      "declinedCountPercent": 69.23,
      "declinedAmountPercent": 72.73,
      "chainCode": "TSTC04",
      "storeNumber": "000000001"
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummaryStore0ErrorException`](../../doc/models/authorizations-summary-store-0-error-exception.md) |


# Get Authorizations Summaryby Chain

Resource to get the summary of authorizations grouped by chains for a given hierarchy and date range with card type and card network being optional parameters. Refer to the schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummarybyChain(
    ?string $vCorrelationId = null,
    ?AuthTransactionsRequestByChain $body = null
): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |
| `body` | [`?AuthTransactionsRequestByChain`](../../doc/models/auth-transactions-request-by-chain.md) | Body, Optional | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SummaryDetailChain`](../../doc/models/summary-detail-chain.md).

## Example Usage

```php
$body = AuthTransactionsRequestByChainBuilder::init(
    EntityBuilder::init()
        ->level(Level::CHAIN)
        ->values(
            [
                'TSTC04',
                'TSTC14',
                'TSTC16'
            ]
        )
        ->build(),
    DateRangeBuilder::init(
        '2024-10-11',
        '2024-11-09'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummarybyChain(
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SummaryDetailChain:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "pagination": {
    "pageNumber": 1,
    "pageSize": 25,
    "totalRowCount": 3,
    "totalReturnedCount": 3
  },
  "totalApprovedCount": 33,
  "totalApprovedAmount": 2895.06,
  "totalDeclinedCount": 66,
  "totalDeclinedAmount": 9276.57,
  "totalApprovedCountPercent": 33.33,
  "totalApprovedAmountPercent": 23.79,
  "totalDeclinedCountPercent": 66.67,
  "totalDeclinedAmountPercent": 76.21,
  "totalCount": 99,
  "totalAmount": 12171.63,
  "summaries": [
    {
      "approvedCount": 33,
      "approvedAmount": 2895.06,
      "declinedCount": 66,
      "declinedAmount": 9276.57,
      "approvedCountPercent": 33.33,
      "approvedAmountPercent": 23.79,
      "declinedCountPercent": 66.67,
      "declinedAmountPercent": 76.21,
      "chainCode": "TSTC04"
    },
    {
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0,
      "chainCode": "TSTC14"
    },
    {
      "approvedCount": 0,
      "approvedAmount": 0,
      "declinedCount": 0,
      "declinedAmount": 0,
      "approvedCountPercent": 0,
      "approvedAmountPercent": 0,
      "declinedCountPercent": 0,
      "declinedAmountPercent": 0,
      "chainCode": "TSTC16"
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummaryChain0ErrorException`](../../doc/models/authorizations-summary-chain-0-error-exception.md) |


# Get Authorizations Summaryby Super Chain

Resource to get the summary of authorizations grouped by superchains for a given hierarchy and date range with card type and card network being optional parameters. Refer to the schema object for the allowed hierarchies and specifications.

```php
function getAuthorizationsSummarybySuperChain(
    ?string $vCorrelationId = null,
    ?AuthTransactionsRequestBySuperChain $body = null
): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `vCorrelationId` | `?string` | Header, Optional | Correlation Id |
| `body` | [`?AuthTransactionsRequestBySuperChain`](../../doc/models/auth-transactions-request-by-super-chain.md) | Body, Optional | - |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SummaryDetailSuperChain`](../../doc/models/summary-detail-super-chain.md).

## Example Usage

```php
$body = AuthTransactionsRequestBySuperChainBuilder::init(
    EntityBuilder::init()
        ->level(Level::SUPERCHAIN)
        ->values(
            [
                'TESTSCBN15'
            ]
        )
        ->build(),
    DateRangeBuilder::init(
        '2024-11-01',
        '2024-11-07'
    )->build()
)->build();

$authorizationsApi = $client->getAuthorizationsApi();
$apiResponse = $authorizationsApi->getAuthorizationsSummarybySuperChain(
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SummaryDetailSuperChain:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "pagination": {
    "pageNumber": 1,
    "pageSize": 25,
    "totalRowCount": 1,
    "totalReturnedCount": 1
  },
  "totalApprovedCount": 11,
  "totalApprovedAmount": 965.02,
  "totalDeclinedCount": 22,
  "totalDeclinedAmount": 3092.19,
  "totalApprovedCountPercent": 33.33,
  "totalApprovedAmountPercent": 23.79,
  "totalDeclinedCountPercent": 66.67,
  "totalDeclinedAmountPercent": 76.21,
  "totalCount": 33,
  "totalAmount": 4057.21,
  "summaries": [
    {
      "approvedCount": 11,
      "approvedAmount": 965.02,
      "declinedCount": 22,
      "declinedAmount": 3092.19,
      "approvedCountPercent": 33.33,
      "approvedAmountPercent": 23.79,
      "declinedCountPercent": 66.67,
      "declinedAmountPercent": 76.21,
      "superChainCode": "TESTSCBN15"
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Default errors | [`AuthorizationsSummarySuperchain0ErrorException`](../../doc/models/authorizations-summary-superchain-0-error-exception.md) |

