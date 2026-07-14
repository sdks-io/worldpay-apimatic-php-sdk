
# Summary Detail Entity Super Chain

*This model accepts additional fields of type array.*

## Structure

`SummaryDetailEntitySuperChain`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `superChainCode` | `?string` | Optional | The identifier code that represents the group of related chains of the partner.<br><br>**Constraints**: *Maximum Length*: `10` | getSuperChainCode(): ?string | setSuperChainCode(?string superChainCode): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\SummaryDetailEntitySuperChainBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$summaryDetailEntitySuperChain = SummaryDetailEntitySuperChainBuilder::init()
    ->superChainCode('AC026')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

