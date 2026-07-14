
# Date Range Type

All dates including and between a specified start and end date. <br> Date range for different hierarchy level:<br><br>07 Days:<br>Independent Sales Organizationn(SO),Independent Sales Affiliate(SA), National(NL), Partner(PT), SuperChain(SC)<br><br>45 days:<br>Chain(CH), Merchant(MT).

*This model accepts additional fields of type array.*

## Structure

`DateRangeType`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `fromDate` | `string` | Required | The starting date of the specified time period.<br><br>**Constraints**: *Minimum Length*: `10`, *Maximum Length*: `10`, *Pattern*: `^[0-9]{4}-[0-9]{2}-[0-9]{2}$` | getFromDate(): string | setFromDate(string fromDate): void |
| `toDate` | `string` | Required | The end date of the specified time period.<br><br>**Constraints**: *Minimum Length*: `10`, *Maximum Length*: `10`, *Pattern*: `^[0-9]{4}-[0-9]{2}-[0-9]{2}$` | getToDate(): string | setToDate(string toDate): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\DateRangeTypeBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$dateRangeType = DateRangeTypeBuilder::init(
    '2016-01-01',
    '2017-08-14'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

