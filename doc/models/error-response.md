
# Error Response

*This model accepts additional fields of type array.*

## Structure

`ErrorResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `errors` | [`?(Error[])`](../../doc/models/error.md) | Optional | The list of errors. | getErrors(): ?array | setErrors(?array errors): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\ErrorResponseBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Builders\ErrorBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$errorResponse = ErrorResponseBuilder::init()
    ->errors(
        [
            ErrorBuilder::init()
                ->errorCode('errorCode6')
                ->errorMessage('errorMessage8')
                ->target('target2')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

