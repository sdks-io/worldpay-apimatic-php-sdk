
# Summary Detail Entity Entity

*This model accepts additional fields of type array.*

## Structure

`SummaryDetailEntityEntity`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `merchantId` | `?string` | Optional | The last level in the Vertical Hierarchy and the unique identifier assigned for a processing location, business type, and MCC Code. It requires a specific value to define merchant authorizations, settlement, reporting, pricing, and billing levels.<br><br>**Constraints**: *Maximum Length*: `16` | getMerchantId(): ?string | setMerchantId(?string merchantId): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Builders\SummaryDetailEntityEntityBuilder;
use ReportingAuthorizationSummaryApiLib\ApiHelper;

$summaryDetailEntityEntity = SummaryDetailEntityEntityBuilder::init()
    ->merchantId('4445091034215')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

