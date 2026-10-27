# Period

The read window, as requested: the report counts from <= t < to. Unlike `costRange`, `to` is not an instant the report covers, so a chart axis ends before it.


## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `From`                                    | [time.Time](https://pkg.go.dev/time#Time) | :heavy_check_mark:                        | Start of the read window, included.       |
| `To`                                      | [time.Time](https://pkg.go.dev/time#Time) | :heavy_check_mark:                        | End of the read window, excluded.         |