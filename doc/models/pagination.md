
# Pagination

*This model accepts additional fields of type array.*

## Structure

`Pagination`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `pageNumber` | `?int` | Optional | The number of the specific page you want to retrieve. <br>Default is page number 01.<br><br>**Default**: `1`<br><br>**Constraints**: `>= 0`, `<= 999999999999999` | getPageNumber(): ?int | setPageNumber(?int pageNumber): void |
| `pageSize` | `?int` | Optional | The number of records that you would want to retrieve per page. <br>Default is 25 items per page.<br><br>**Default**: `25`<br><br>**Constraints**: `>= 0`, `<= 999999999999999` | getPageSize(): ?int | setPageSize(?int pageSize): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\PaginationBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$pagination = PaginationBuilder::init()
    ->pageNumber(2)
    ->pageSize(10)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

