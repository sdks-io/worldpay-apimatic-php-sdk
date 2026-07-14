
# Auth Transactions Request

*This model accepts additional fields of type array.*

## Structure

`AuthTransactionsRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `hierarchy` | [`Entity`](../../doc/models/entity.md) | Required | - | getHierarchy(): Entity | setHierarchy(Entity hierarchy): void |
| `cardType` | `?string` | Optional | The category or classification of a payment card based on the issuing network. Default is Credit.<br>Debit isn't supported in this release.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` | getCardType(): ?string | setCardType(?string cardType): void |
| `cardNetworks` | [`?(string(CardNetworkType)[])`](../../doc/models/card-network-type.md) | Optional | The network the card is associated with that facilitates the payment. <br>Default is All Card Networks. | getCardNetworks(): ?array | setCardNetworks(?array cardNetworks): void |
| `dateRange` | [`DateRange`](../../doc/models/date-range.md) | Required | - | getDateRange(): DateRange | setDateRange(DateRange dateRange): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\AuthTransactionsRequestBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Builders\EntityBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Level;
use ReportingAuthorizationSummaryApiLib\ApiHelper;
use ReportingAuthorizationSummaryApiLib\Models\Builders\DateRangeBuilder;
use ReportingAuthorizationSummaryApiLib\Models\CardNetworkType;

$authTransactionsRequest = AuthTransactionsRequestBuilder::init(
    EntityBuilder::init()
        ->level(Level::MERCHANT)
        ->values(
            [
                '4445000123456',
                '4445000234567'
            ]
        )
        ->chainCode('1X0010')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    DateRangeBuilder::init(
        '2016-01-01',
        '2017-08-14'
    )
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build()
)
    ->cardType('CREDIT')
    ->cardNetworks(
        [
            CardNetworkType::WRIGHT_EXPRESS
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

