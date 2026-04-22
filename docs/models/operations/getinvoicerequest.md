# GetInvoiceRequest


## Fields

| Field                                                                   | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `ID`                                                                    | `string`                                                                | :heavy_check_mark:                                                      | The invoice ID                                                          |
| `Expand`                                                                | `*string`                                                               | :heavy_minus_sign:                                                      | Comma-separated list of fields to expand. Currently supports: lineItems |
| `LineItemsLimit`                                                        | `*int64`                                                                | :heavy_minus_sign:                                                      | Page size for line items when expand=lineItems                          |
| `LineItemsPageToken`                                                    | `*string`                                                               | :heavy_minus_sign:                                                      | Pagination token for line items when expand=lineItems                   |