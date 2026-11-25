# CreditPoolLedgerPeriod

This bucket's calendar-aligned period (UTC). The first and last bucket in the response are clamped to the requested `from`/`to` rather than the full calendar period.


## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `From`                                    | [time.Time](https://pkg.go.dev/time#Time) | :heavy_check_mark:                        | N/A                                       |
| `To`                                      | [time.Time](https://pkg.go.dev/time#Time) | :heavy_check_mark:                        | N/A                                       |