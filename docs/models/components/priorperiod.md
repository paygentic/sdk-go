# PriorPeriod

Prior-period comparison data. Present only when comparePriorPeriod=true.


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `Cost`                                                               | `float64`                                                            | :heavy_check_mark:                                                   | N/A                                                                  |
| `ChangePercent`                                                      | `*float64`                                                           | :heavy_check_mark:                                                   | Percentage change vs prior period. Null when prior period cost is 0. |