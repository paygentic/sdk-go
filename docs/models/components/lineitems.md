# LineItems

Line items (only present if expand=lineItems query parameter is provided)


## Fields

| Field                                                                      | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `InvoiceID`                                                                | `string`                                                                   | :heavy_check_mark:                                                         | The invoice ID                                                             |
| `LineItems`                                                                | [][components.InvoiceLineItem](../../models/components/invoicelineitem.md) | :heavy_check_mark:                                                         | Array of line items for this page                                          |
| `NextPageToken`                                                            | optionalnullable.OptionalNullable[`string`]                                | :heavy_minus_sign:                                                         | Token for fetching the next page, null if no more pages                    |
| `TotalCount`                                                               | `int64`                                                                    | :heavy_check_mark:                                                         | Total number of line items across all pages                                |