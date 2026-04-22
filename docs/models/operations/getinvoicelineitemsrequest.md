# GetInvoiceLineItemsRequest


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `ID`                                                   | `string`                                               | :heavy_check_mark:                                     | The invoice ID                                         |
| `Limit`                                                | `*int64`                                               | :heavy_minus_sign:                                     | Maximum number of line items to return                 |
| `PageToken`                                            | `*string`                                              | :heavy_minus_sign:                                     | Token for pagination to fetch the next page of results |