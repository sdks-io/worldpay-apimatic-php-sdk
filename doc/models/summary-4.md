
# Summary 4

*This model accepts additional fields of type array.*

## Structure

`Summary4`

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
| `merchantId` | `?string` | Optional | The last level in the Vertical Hierarchy and the unique identifier assigned for a processing location, business type, and MCC Code. It requires a specific value to define merchant authorizations, settlement, reporting, pricing, and billing levels.<br><br>**Constraints**: *Maximum Length*: `16` | getMerchantId(): ?string | setMerchantId(?string merchantId): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\Summary4Builder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$summary4 = Summary4Builder::init()
    ->approvedCount(10)
    ->approvedAmount(120.04)
    ->declinedCount(11)
    ->declinedAmount(20.09)
    ->approvedCountPercent(47.12)
    ->approvedAmountPercent(85.98)
    ->declinedCountPercent(52.45)
    ->declinedAmountPercent(14.65)
    ->merchantId('4445091034215')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

