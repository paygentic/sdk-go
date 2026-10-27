# Stale

Present only when the database can't be reached, or the list takes more than a second to compute. The response is then the last result for this same request in the past hour, computed at `computedAt`.


## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `ComputedAt`                              | [time.Time](https://pkg.go.dev/time#Time) | :heavy_check_mark:                        | When this result was computed.            |