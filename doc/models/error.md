
# Error

Error Message

*This model accepts additional fields of type array.*

## Structure

`Error`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `errorCode` | `?string` | Optional | The error code.<br><br>**Constraints**: *Maximum Length*: `256` | getErrorCode(): ?string | setErrorCode(?string errorCode): void |
| `errorMessage` | `?string` | Optional | Error message<br><br>**Constraints**: *Maximum Length*: `256` | getErrorMessage(): ?string | setErrorMessage(?string errorMessage): void |
| `target` | `?string` | Optional | Error target<br><br>**Constraints**: *Maximum Length*: `256` | getTarget(): ?string | setTarget(?string target): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\ErrorBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$error = ErrorBuilder::init()
    ->errorCode('ERROR_CODE')
    ->errorMessage('Error message here.')
    ->target('Target field name.')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

