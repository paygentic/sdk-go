# PaymentSummary


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `CompletedCount`                                   | `int64`                                            | :heavy_check_mark:                                 | Number of completed payment links in the period    |
| `CompletedAmount`                                  | `string`                                           | :heavy_check_mark:                                 | Total amount of completed payment links in dollars |
| `PendingCount`                                     | `int64`                                            | :heavy_check_mark:                                 | Number of pending payment links in the period      |
| `PendingAmount`                                    | `string`                                           | :heavy_check_mark:                                 | Total amount of pending payment links in dollars   |
| `ExpiredCount`                                     | `int64`                                            | :heavy_check_mark:                                 | Number of expired payment links in the period      |
| `ExpiredAmount`                                    | `string`                                           | :heavy_check_mark:                                 | Total amount of expired payment links in dollars   |