# Tax

Tax reconciliation metadata (only present when plan has taxEnabled)


## Fields

| Field                                                           | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `ActualTax`                                                     | `*string`                                                       | :heavy_minus_sign:                                              | Actual tax calculated (in atomic units)                         |
| `AdjustmentApplied`                                             | `*bool`                                                         | :heavy_minus_sign:                                              | Whether wallet adjustment was applied during tax reconciliation |
| `AdjustmentNeeded`                                              | `*bool`                                                         | :heavy_minus_sign:                                              | Whether wallet adjustment is needed (difference >= $0.01)       |
| `Difference`                                                    | `*string`                                                       | :heavy_minus_sign:                                              | Difference between actual and estimated (in atomic units)       |
| `EstimatedTax`                                                  | `*string`                                                       | :heavy_minus_sign:                                              | Tax estimated from subscription rate (in atomic units)          |
| `Reconciled`                                                    | `*bool`                                                         | :heavy_minus_sign:                                              | Whether reconciliation was performed                            |
| `ReconciledAt`                                                  | [*time.Time](https://pkg.go.dev/time#Time)                      | :heavy_minus_sign:                                              | When reconciliation occurred                                    |