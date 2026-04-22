# GetBillableMetricMeterRequest


## Fields

| Field                                                           | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `ID`                                                            | `string`                                                        | :heavy_check_mark:                                              | N/A                                                             |
| `From`                                                          | [time.Time](https://pkg.go.dev/time#Time)                       | :heavy_check_mark:                                              | Start of query window (ISO 8601)                                |
| `To`                                                            | [time.Time](https://pkg.go.dev/time#Time)                       | :heavy_check_mark:                                              | End of query window (ISO 8601)                                  |
| `Subject`                                                       | `*string`                                                       | :heavy_minus_sign:                                              | Filter by customer/user ID                                      |
| `WindowSize`                                                    | [*operations.WindowSize](../../models/operations/windowsize.md) | :heavy_minus_sign:                                              | Time bucket granularity                                         |
| `FilterGroupBy`                                                 | `*string`                                                       | :heavy_minus_sign:                                              | JSON-encoded dimension filter (e.g. {"key":"value"})            |
| `GroupBy`                                                       | `*string`                                                       | :heavy_minus_sign:                                              | Comma-separated dimension keys                                  |