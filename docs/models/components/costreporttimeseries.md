# CostReportTimeSeries


## Fields

| Field                                                                               | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `WindowStart`                                                                       | [time.Time](https://pkg.go.dev/time#Time)                                           | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `WindowEnd`                                                                         | [time.Time](https://pkg.go.dev/time#Time)                                           | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `Groups`                                                                            | map[string]`float64`                                                                | :heavy_check_mark:                                                                  | Map of group key → cost value for this time window. Keys match CostReportGroup.key. |