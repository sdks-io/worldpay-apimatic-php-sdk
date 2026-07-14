
# Entity Store Response

*This model accepts additional fields of type array.*

## Structure

`EntityStoreResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `chainCode` | `?string` | Optional | The level of the merchant hierarchy that groups merchant identifiers (MIDs) and any related roll-up values under a common identifier for settlement, billing, and reporting. Chain Code is the primary identifier for merchants boarded in a MDB (Merchant Database) system.<br><br>**Constraints**: *Maximum Length*: `6` | getChainCode(): ?string | setChainCode(?string chainCode): void |
| `storeNumber` | `?string` | Optional | The lowest roll-up level in the hierarchy system, grouping multiple merchant account numbers (MIDs) used in a single merchant location assigned to different terminals and/or business lines (MCCs). A Store Number is nine digits and unique to a particular Chain, meaning the same Store Number can exist for a Store under a different Divison/Chain, but not duplicates under the same Divison/Chain. <br> Supports entities Chain, National.<br><br>**Constraints**: *Maximum Length*: `9` | getStoreNumber(): ?string | setStoreNumber(?string storeNumber): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\EntityStoreResponseBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$entityStoreResponse = EntityStoreResponseBuilder::init()
    ->chainCode('1X0010')
    ->storeNumber('000000001')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

