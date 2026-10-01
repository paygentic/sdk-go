# ListIntervalChangesRequest


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `Limit`                                                             | `*string`                                                           | :heavy_minus_sign:                                                  | Number of interval changes to return                                |
| `Offset`                                                            | `*string`                                                           | :heavy_minus_sign:                                                  | Number of interval changes to skip                                  |
| `From`                                                              | [*time.Time](https://pkg.go.dev/time#Time)                          | :heavy_minus_sign:                                                  | Only return changes recorded at or after this time                  |
| `To`                                                                | [*time.Time](https://pkg.go.dev/time#Time)                          | :heavy_minus_sign:                                                  | Only return changes recorded before this time                       |
| `ChangeReason`                                                      | [*components.ChangeReason](../../models/components/changereason.md) | :heavy_minus_sign:                                                  | Only return changes with this reason.                               |