# ListBillableMetricsRequest


## Fields

| Field                                                | Type                                                 | Required                                             | Description                                          |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| `Limit`                                              | `*int64`                                             | :heavy_minus_sign:                                   | Number of billable metrics to return.                |
| `MerchantID`                                         | `string`                                             | :heavy_check_mark:                                   | Filter billable metrics by merchant organization ID. |
| `Offset`                                             | `*int64`                                             | :heavy_minus_sign:                                   | Number of billable metrics to skip.                  |
| `ProductID`                                          | `*string`                                            | :heavy_minus_sign:                                   | Filter billable metrics by product ID.               |