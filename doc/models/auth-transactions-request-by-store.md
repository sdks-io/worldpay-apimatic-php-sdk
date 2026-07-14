
# Auth Transactions Request by Store

*This model accepts additional fields of type array.*

## Structure

`AuthTransactionsRequestByStore`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `pagination` | [`?Pagination`](../../doc/models/pagination.md) | Optional | - | getPagination(): ?Pagination | setPagination(?Pagination pagination): void |
| `hierarchy` | [`Entity`](../../doc/models/entity.md) | Required | - | getHierarchy(): Entity | setHierarchy(Entity hierarchy): void |
| `cardType` | `?string` | Optional | The category or classification of a payment card based on the issuing network. Default is Credit.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` | getCardType(): ?string | setCardType(?string cardType): void |
| `cardNetworks` | [`?(string(CardNetworkType)[])`](../../doc/models/card-network-type.md) | Optional | The network the card is associated with that facilitates the payment. <br>Default is All Card Networks. | getCardNetworks(): ?array | setCardNetworks(?array cardNetworks): void |
| `dateRange` | [`DateRange`](../../doc/models/date-range.md) | Required | - | getDateRange(): DateRange | setDateRange(DateRange dateRange): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\AuthTransactionsRequestByStoreBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Builders\EntityBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Level;
use ReportingAuthorizationSummaryApiLib\ApiHelper;
use ReportingAuthorizationSummaryApiLib\Models\Builders\DateRangeBuilder;
use ReportingAuthorizationSummaryApiLib\Models\Builders\PaginationBuilder;
use ReportingAuthorizationSummaryApiLib\Models\CardNetworkType;

$authTransactionsRequestByStore = AuthTransactionsRequestByStoreBuilder::init(
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
    ->pagination(
        PaginationBuilder::init()
            ->pageNumber(106)
            ->pageSize(134)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->cardType('CREDIT')
    ->cardNetworks(
        [
            CardNetworkType::MASTERCARD,
            CardNetworkType::DISCOVER
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

