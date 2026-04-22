# LineItem


## Fields

| Field                                             | Type                                              | Required                                          | Description                                       |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `Description`                                     | `string`                                          | :heavy_check_mark:                                | Line item description.                            |
| `Amount`                                          | `string`                                          | :heavy_check_mark:                                | Line item amount in decimal format (e.g. '5.00'). |
| `Quantity`                                        | `*int64`                                          | :heavy_minus_sign:                                | Quantity of this line item. Defaults to 1.        |