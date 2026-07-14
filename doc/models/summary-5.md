
# Summary 5

*This model accepts additional fields of type array.*

## Structure

`Summary5`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `approvedCount` | `?int` | Optional | Count of the approved transactions.<br><br>**Constraints**: `<= 9999999999` | getApprovedCount(): ?int | setApprovedCount(?int approvedCount): void |
| `approvedAmount` | `?float` | Optional | Sum of the amount of approved transactions.<br><br>**Constraints**: `<= 999999999999999` | getApprovedAmount(): ?float | setApprovedAmount(?float approvedAmount): void |
| `declinedCount` | `?int` | Optional | Count of the declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getDeclinedCount(): ?int | setDeclinedCount(?int declinedCount): void |
| `declinedAmount` | `?float` | Optional | Sum of the amount of the declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getDeclinedAmount(): ?float | setDeclinedAmount(?float declinedAmount): void |
| `approvedCountPercent` | `?float` | Optional | Ratio of the count of the approved transactions to the count of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getApprovedCountPercent(): ?float | setApprovedCountPercent(?float approvedCountPercent): void |
| `approvedAmountPercent` | `?float` | Optional | Ratio of the sum of the amount of approved transactions to the sum of the amount of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getApprovedAmountPercent(): ?float | setApprovedAmountPercent(?float approvedAmountPercent): void |
| `declinedCountPercent` | `?float` | Optional | Ratio of the count of the declined transactions to the count of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getDeclinedCountPercent(): ?float | setDeclinedCountPercent(?float declinedCountPercent): void |
| `declinedAmountPercent` | `?float` | Optional | Ratio of the sum of the amount of declined transactions to the sum of the amount of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getDeclinedAmountPercent(): ?float | setDeclinedAmountPercent(?float declinedAmountPercent): void |
| `chainCode` | `?string` | Optional | The level of the merchant hierarchy that groups merchant identifiers (MIDs) and any related roll-up values under a common identifier for settlement, billing, and reporting. Chain Code is the primary identifier for merchants boarded in a MDB (Merchant Database) system.<br><br>**Constraints**: *Maximum Length*: `6` | getChainCode(): ?string | setChainCode(?string chainCode): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\Summary5Builder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$summary5 = Summary5Builder::init()
    ->approvedCount(10)
    ->approvedAmount(120.04)
    ->declinedCount(11)
    ->declinedAmount(20.09)
    ->approvedCountPercent(47.12)
    ->approvedAmountPercent(85.98)
    ->declinedCountPercent(52.45)
    ->declinedAmountPercent(14.65)
    ->chainCode('1X0010')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

