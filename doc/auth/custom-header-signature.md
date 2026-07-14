
# Custom Header Signature



Documentation for accessing and setting credentials for api_key.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| Authorization | `string` | ` License format is WORLDPAY license='xxxx'` | `authorization` | `getAuthorization()` |



**Note:** Auth credentials can be set using `CustomHeaderAuthenticationCredentialsBuilder::init()` in `customHeaderAuthenticationCredentials` method in the client builder and accessed through `getCustomHeaderAuthenticationCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```php
use ReportingAuthorizationSummaryApiLib\Authentication\CustomHeaderAuthenticationCredentialsBuilder;
use ReportingAuthorizationSummaryApiLib\ReportingAuthorizationSummaryApiClientBuilder;

$client = ReportingAuthorizationSummaryApiClientBuilder::init()
    ->customHeaderAuthenticationCredentials(
        CustomHeaderAuthenticationCredentialsBuilder::init(
            'Authorization'
        )
    )
    ->build();
```


