
# Summary Responses

*This model accepts additional fields of type array.*

## Structure

`SummaryResponses`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `totalApprovedCount` | `?int` | Optional | Count of approved transactions.<br><br>**Constraints**: `<= 9999999999` | getTotalApprovedCount(): ?int | setTotalApprovedCount(?int totalApprovedCount): void |
| `totalApprovedAmount` | `?float` | Optional | Sum of the approved transactions.<br><br>**Constraints**: `<= 999999999999999` | getTotalApprovedAmount(): ?float | setTotalApprovedAmount(?float totalApprovedAmount): void |
| `totalDeclinedCount` | `?int` | Optional | Count of declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getTotalDeclinedCount(): ?int | setTotalDeclinedCount(?int totalDeclinedCount): void |
| `totalDeclinedAmount` | `?float` | Optional | Sum of the declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getTotalDeclinedAmount(): ?float | setTotalDeclinedAmount(?float totalDeclinedAmount): void |
| `totalApprovedCountPercent` | `?float` | Optional | Ratio of the count of approved transactions to the count of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalApprovedCountPercent(): ?float | setTotalApprovedCountPercent(?float totalApprovedCountPercent): void |
| `totalApprovedAmountPercent` | `?float` | Optional | Ratio of the sum of the amount of approved transactions to the sum of the amount of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalApprovedAmountPercent(): ?float | setTotalApprovedAmountPercent(?float totalApprovedAmountPercent): void |
| `totalDeclinedCountPercent` | `?float` | Optional | Ratio of the count of declined transactions to the count of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalDeclinedCountPercent(): ?float | setTotalDeclinedCountPercent(?float totalDeclinedCountPercent): void |
| `totalDeclinedAmountPercent` | `?float` | Optional | Ratio of the sum of the amount of declined transactions to the sum of the amount of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalDeclinedAmountPercent(): ?float | setTotalDeclinedAmountPercent(?float totalDeclinedAmountPercent): void |
| `totalCount` | `?int` | Optional | Sum of the count of approved transactions and the count of declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getTotalCount(): ?int | setTotalCount(?int totalCount): void |
| `totalAmount` | `?float` | Optional | Sum of the amount of approved transactions and the amount of declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getTotalAmount(): ?float | setTotalAmount(?float totalAmount): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\SummaryResponsesBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$summaryResponses = SummaryResponsesBuilder::init()
    ->totalApprovedCount(10)
    ->totalApprovedAmount(120.01)
    ->totalDeclinedCount(11)
    ->totalDeclinedAmount(20.02)
    ->totalApprovedCountPercent(47.12)
    ->totalApprovedAmountPercent(85.98)
    ->totalDeclinedCountPercent(52.45)
    ->totalDeclinedAmountPercent(14.65)
    ->totalCount(21)
    ->totalAmount(140.01)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

