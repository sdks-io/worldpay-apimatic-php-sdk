
# Getting Started with Reporting: Authorization Summary API

## Introduction

Retrieves authorized summaries and supports group by operations.

## Install the Package

Run the following command to install the package and automatically add the dependency to your composer.json file:

```bash
composer require "worldpay-apimatic/worldpay-apimatic-sdk:0.0.2"
```

Or add it to the composer.json file manually as given below:

```json
"require": {
    "worldpay-apimatic/worldpay-apimatic-sdk": "0.0.2"
}
```

You can also view the package at:
https://packagist.org/packages/worldpay-apimatic/worldpay-apimatic-sdk#0.0.2

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| customHeaderAuthenticationCredentials | [`CustomHeaderAuthenticationCredentials`](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |

The API client can be initialized as follows:

```php
use ReportingAuthorizationSummaryApiLib\Logging\LoggingConfigurationBuilder;
use ReportingAuthorizationSummaryApiLib\Logging\RequestLoggingConfigurationBuilder;
use ReportingAuthorizationSummaryApiLib\Logging\ResponseLoggingConfigurationBuilder;
use Psr\Log\LogLevel;
use ReportingAuthorizationSummaryApiLib\Authentication\CustomHeaderAuthenticationCredentialsBuilder;
use ReportingAuthorizationSummaryApiLib\ReportingAuthorizationSummaryApiClientBuilder;

$client = ReportingAuthorizationSummaryApiClientBuilder::init()
    ->customHeaderAuthenticationCredentials(
        CustomHeaderAuthenticationCredentialsBuilder::init(
            'Authorization'
        )
    )
    ->loggingConfiguration(
        LoggingConfigurationBuilder::init()
            ->level(LogLevel::INFO)
            ->requestConfiguration(RequestLoggingConfigurationBuilder::init()->body(true))
            ->responseConfiguration(ResponseLoggingConfigurationBuilder::init()->headers(true))
    )
    ->build();
```

## Authorization

This API uses the following authentication schemes.

* [`api_key (Custom Header Signature)`](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/auth/custom-header-signature.md)

## List of APIs

* [Authorizations](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/controllers/authorizations.md)

## SDK Infrastructure

### Configuration

* [ProxyConfigurationBuilder](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/proxy-configuration-builder.md)
* [LoggingConfigurationBuilder](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/logging-configuration-builder.md)
* [RequestLoggingConfigurationBuilder](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/request-logging-configuration-builder.md)
* [ResponseLoggingConfigurationBuilder](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/response-logging-configuration-builder.md)

### HTTP

* [HttpRequest](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/http-request.md)

### Utilities

* [ApiResponse](https://www.github.com/sdks-io/worldpay-apimatic-php-sdk/tree/0.0.2/doc/api-response.md)

