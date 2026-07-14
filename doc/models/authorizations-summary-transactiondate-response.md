
# Authorizations Summary Transactiondate Response

*This model accepts additional fields of type array.*

## Structure

`AuthorizationsSummaryTransactiondateResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `pagination` | [`?PaginationResponse`](../../doc/models/pagination-response.md) | Optional | - | getPagination(): ?PaginationResponse | setPagination(?PaginationResponse pagination): void |
| `totalApprovedCount` | `?int` | Optional | Count of the approved transactions.<br><br>**Constraints**: `<= 9999999999` | getTotalApprovedCount(): ?int | setTotalApprovedCount(?int totalApprovedCount): void |
| `totalApprovedAmount` | `?float` | Optional | Sum of the amount of approved transactions.<br><br>**Constraints**: `<= 9999999999` | getTotalApprovedAmount(): ?float | setTotalApprovedAmount(?float totalApprovedAmount): void |
| `totalDeclinedCount` | `?int` | Optional | Count of the declined transactions.<br><br>**Constraints**: `<= 9999999999` | getTotalDeclinedCount(): ?int | setTotalDeclinedCount(?int totalDeclinedCount): void |
| `totalDeclinedAmount` | `?float` | Optional | Sum of the amount of declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getTotalDeclinedAmount(): ?float | setTotalDeclinedAmount(?float totalDeclinedAmount): void |
| `totalApprovedCountPercent` | `?float` | Optional | Ratio of the count of approved transactions to the count of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalApprovedCountPercent(): ?float | setTotalApprovedCountPercent(?float totalApprovedCountPercent): void |
| `totalApprovedAmountPercent` | `?float` | Optional | Ratio of the sum of the amount of the approved transactions to the sum of amount of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalApprovedAmountPercent(): ?float | setTotalApprovedAmountPercent(?float totalApprovedAmountPercent): void |
| `totalDeclinedCountPercent` | `?float` | Optional | Ratio of the count of the declined transactions to the count of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalDeclinedCountPercent(): ?float | setTotalDeclinedCountPercent(?float totalDeclinedCountPercent): void |
| `totalDeclinedAmountPercent` | `?float` | Optional | Ratio of the sum of the amount of the declined transactions to the sum of the amount of total transctions.<br><br>**Constraints**: `<= 999999999999999` | getTotalDeclinedAmountPercent(): ?float | setTotalDeclinedAmountPercent(?float totalDeclinedAmountPercent): void |
| `totalCount` | `?int` | Optional | Sum of the count of the approved transactions and the count of the declined transactions.<br><br>**Constraints**: `<= 9999999999` | getTotalCount(): ?int | setTotalCount(?int totalCount): void |
| `totalAmount` | `?float` | Optional | Sum of the amount of approved transactions and the amount of the declined transactions.<br><br>**Constraints**: `<= 999999999999999` | getTotalAmount(): ?float | setTotalAmount(?float totalAmount): void |
| `summaries` | [`?(Summary1[])`](../../doc/models/summary-1.md) | Optional | Capturing the fields. | getSummaries(): ?array | setSummaries(?array summaries): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\AuthorizationsSummaryTransactiondateResponseBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Builders\PaginationResponseBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$authorizationsSummaryTransactiondateResponse = AuthorizationsSummaryTransactiondateResponseBuilder::init()
    ->pagination(
        PaginationResponseBuilder::init()
            ->pageNumber(106)
            ->pageSize(134)
            ->totalRowCount(22)
            ->totalReturnedCount(172)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
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

