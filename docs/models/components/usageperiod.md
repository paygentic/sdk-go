# UsagePeriod


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `Interval`                                                       | `string`                                                         | :heavy_check_mark:                                               | ISO 8601 duration for the usage period, e.g. P1D, P1W, P1M, P1Y. |
| `Anchor`                                                         | [*time.Time](https://pkg.go.dev/time#Time)                       | :heavy_minus_sign:                                               | Optional anchor date-time for period alignment.                  |