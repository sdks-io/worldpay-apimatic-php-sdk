
# Date Range

*This model accepts additional fields of type array.*

## Structure

`DateRange`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `fromDate` | `string` | Required | The starting date of the specified time period.<br><br>**Constraints**: *Minimum Length*: `10`, *Maximum Length*: `10`, *Pattern*: `^[0-9]{4}-[0-9]{2}-[0-9]{2}$` | getFromDate(): string | setFromDate(string fromDate): void |
| `toDate` | `string` | Required | The end date of the specified time period.<br><br>**Constraints**: *Minimum Length*: `10`, *Maximum Length*: `10`, *Pattern*: `^[0-9]{4}-[0-9]{2}-[0-9]{2}$` | getToDate(): string | setToDate(string toDate): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\DateRangeBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$dateRange = DateRangeBuilder::init(
    '2016-01-01',
    '2017-08-14'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

