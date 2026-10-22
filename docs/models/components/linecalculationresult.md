# LineCalculationResult

Equal to the line's stored amount, quantity and unit price.


## Fields

| Field                                                                                              | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `Amount`                                                                                           | `string`                                                                                           | :heavy_check_mark:                                                                                 | The line's amount before tax.                                                                      |
| `Quantity`                                                                                         | `*string`                                                                                          | :heavy_check_mark:                                                                                 | The line's quantity.                                                                               |
| `UnitPrice`                                                                                        | `*string`                                                                                          | :heavy_check_mark:                                                                                 | The line's unit price. It can be rounded, so quantity times unit price can differ from the amount. |