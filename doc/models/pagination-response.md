
# Pagination Response

*This model accepts additional fields of type array.*

## Structure

`PaginationResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `pageNumber` | `?int` | Optional | The number of the specific page you want to retrieve.<br><br>**Constraints**: `>= 0`, `<= 999999999999999` | getPageNumber(): ?int | setPageNumber(?int pageNumber): void |
| `pageSize` | `?int` | Optional | The number of records that you would want to retrieve per page.<br><br>**Constraints**: `>= 0`, `<= 999999999999999` | getPageSize(): ?int | setPageSize(?int pageSize): void |
| `totalRowCount` | `?int` | Optional | The total number of result rows returned.<br><br>**Constraints**: `>= 0`, `<= 999999999999999` | getTotalRowCount(): ?int | setTotalRowCount(?int totalRowCount): void |
| `totalReturnedCount` | `?int` | Optional | The total number of records returned.<br><br>**Constraints**: `>= 0`, `<= 999999999999999` | getTotalReturnedCount(): ?int | setTotalReturnedCount(?int totalReturnedCount): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\PaginationResponseBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$paginationResponse = PaginationResponseBuilder::init()
    ->pageNumber(1)
    ->pageSize(50)
    ->totalRowCount(85)
    ->totalReturnedCount(25)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

