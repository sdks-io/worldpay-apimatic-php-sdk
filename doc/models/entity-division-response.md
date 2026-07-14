
# Entity Division Response

*This model accepts additional fields of type array.*

## Structure

`EntityDivisionResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `chainCode` | `?string` | Optional | The level of the merchant hierarchy that groups merchant identifiers (MIDs) and any related roll-up values under a common identifier for settlement, billing, and reporting. Chain Code is the primary identifier for merchants boarded in a MDB (Merchant Database) system.<br><br>**Constraints**: *Maximum Length*: `6` | getChainCode(): ?string | setChainCode(?string chainCode): void |
| `divisionNumber` | `?string` | Optional | The hierarchy level that enables merchants to roll-up child entities for Stores/Locations into different groups under a Chain. It is an optional hierarchy level, but if created, is required for all child entities under the Division Number which is unique to that particular Chain. <br> Supports entities Chain, National.<br><br>**Constraints**: *Maximum Length*: `3` | getDivisionNumber(): ?string | setDivisionNumber(?string divisionNumber): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\EntityDivisionResponseBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$entityDivisionResponse = EntityDivisionResponseBuilder::init()
    ->chainCode('1X0010')
    ->divisionNumber('088')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

