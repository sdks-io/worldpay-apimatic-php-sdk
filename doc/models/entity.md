
# Entity

*This model accepts additional fields of type array.*

## Structure

`Entity`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `level` | [`?string(Level)`](../../doc/models/level.md) | Optional | - | getLevel(): ?string | setLevel(?string level): void |
| `values` | `?(string[])` | Optional | Refers to hierarchy id. Accepts a list of ids.<br><br>**Constraints**: *Maximum Length*: `255` | getValues(): ?array | setValues(?array values): void |
| `chainCode` | `?string` | Optional | The level of the merchant hierarchy that groups merchant identifiers (MIDs) and any related roll-up values under a common identifier for settlement, billing, and reporting. Chain Code is the primary identifier for merchants boarded in a MDB (Merchant Database) system. <br> Chain code is mandatory when the hierarchy level selected is Store or Division.<br><br>**Constraints**: *Maximum Length*: `6` | getChainCode(): ?string | setChainCode(?string chainCode): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\EntityBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Level;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$entity = EntityBuilder::init()
    ->level(Level::INDEPENDENT_SALES_ORGANIZATION)
    ->values(
        [
            '4445000123456',
            '4445000234567'
        ]
    )
    ->chainCode('1X0010')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

