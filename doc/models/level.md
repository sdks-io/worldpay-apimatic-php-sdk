
# Level

Supports entities such as Independent Sales Organization and Independent Sales Channel with a limit of one entity, <br>National, SuperChain, Partner with a maximum limit of 10 entities, <br>Chain, Division, Store, and Merchant with a maximum limit of 2000 entities.

## Enumeration

`Level`

## Fields

| Name |
|  --- |
| `MERCHANT` |
| `STORE` |
| `DIVISION` |
| `CHAIN` |
| `PARTNER` |
| `SUPERCHAIN` |
| `NATIONAL` |
| `INDEPENDENT_SALES_CHANNEL` |
| `INDEPENDENT_SALES_ORGANIZATION` |

## Example

```php
use ReportingAuthorizationSummaryApiLib\Models\Level;

$level = Level::INDEPENDENT_SALES_CHANNEL;
```

