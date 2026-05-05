# ProfitabilityTrend


## Fields

| Field                                                                              | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `Values`                                                                           | []`string`                                                                         | :heavy_check_mark:                                                                 | Revenue values per time bucket, oldest first, in unit currency with two decimals.  |
| `PeriodChange`                                                                     | `*float64`                                                                         | :heavy_check_mark:                                                                 | Period-over-period % change (current half vs prior half). Null when prior is zero. |