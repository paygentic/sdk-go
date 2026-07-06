# CreateOrderLineItemRequest


## Fields

| Field                                       | Type                                        | Required                                    | Description                                 |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| `ItemID`                                    | optionalnullable.OptionalNullable[`string`] | :heavy_minus_sign:                          | N/A                                         |
| `Description`                               | optionalnullable.OptionalNullable[`string`] | :heavy_minus_sign:                          | N/A                                         |
| `Quantity`                                  | `string`                                    | :heavy_check_mark:                          | N/A                                         |
| `ListUnitPrice`                             | `string`                                    | :heavy_check_mark:                          | N/A                                         |
| `DiscountUnitAmount`                        | `*string`                                   | :heavy_minus_sign:                          | N/A                                         |
| `UnitPrice`                                 | `string`                                    | :heavy_check_mark:                          | N/A                                         |
| `TotalPrice`                                | `string`                                    | :heavy_check_mark:                          | N/A                                         |
| `Metadata`                                  | map[string]`any`                            | :heavy_minus_sign:                          | N/A                                         |
| `TermStartDate`                             | [*time.Time](https://pkg.go.dev/time#Time)  | :heavy_minus_sign:                          | N/A                                         |
| `TermEndDate`                               | [*time.Time](https://pkg.go.dev/time#Time)  | :heavy_minus_sign:                          | N/A                                         |