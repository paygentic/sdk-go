# SubscriptionCreateOverridePriceOp

A rate or quantity override for a price the plan version carries. Supply at least one of unitPrice or baseQuantity; a request supplying neither is rejected with a 400 naming the entry.


## Fields

| Field                                                                       | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `OverridesPriceID`                                                          | `string`                                                                    | :heavy_check_mark:                                                          | The plan-version price being overridden. Its priceKey lineage is preserved. |
| `UnitPrice`                                                                 | `*string`                                                                   | :heavy_minus_sign:                                                          | The agreed rate, as a decimal string.                                       |
| `BaseQuantity`                                                              | `*string`                                                                   | :heavy_minus_sign:                                                          | The agreed quantity, as a decimal string.                                   |