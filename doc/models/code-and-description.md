
# Code and Description

*This model accepts additional fields of type array.*

## Structure

`CodeAndDescription`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `code` | `?string` | Optional | The code.<br><br>**Constraints**: *Maximum Length*: `3` | getCode(): ?string | setCode(?string code): void |
| `shortDescription` | `?string` | Optional | Short description.<br><br>**Constraints**: *Maximum Length*: `255` | getShortDescription(): ?string | setShortDescription(?string shortDescription): void |
| `longDescription` | `?string` | Optional | Long description.<br><br>**Constraints**: *Maximum Length*: `255` | getLongDescription(): ?string | setLongDescription(?string longDescription): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\CodeAndDescriptionBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$codeAndDescription = CodeAndDescriptionBuilder::init()
    ->code('code4')
    ->shortDescription('shortDescription8')
    ->longDescription('longDescription6')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

