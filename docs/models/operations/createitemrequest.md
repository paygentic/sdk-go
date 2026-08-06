# CreateItemRequest


## Fields

| Field                                | Type                                 | Required                             | Description                          |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `MerchantID`                         | `string`                             | :heavy_check_mark:                   | N/A                                  |
| `Name`                               | `string`                             | :heavy_check_mark:                   | Canonical sellable name for the Item |
| `CatalogID`                          | `*string`                            | :heavy_minus_sign:                   | Unique identifier for a product      |
| `Metadata`                           | map[string]`any`                     | :heavy_minus_sign:                   | Optional key-value metadata          |