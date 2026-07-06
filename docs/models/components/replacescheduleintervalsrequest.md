# ReplaceScheduleIntervalsRequest


## Fields

| Field                                                                            | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `Intervals`                                                                      | [][components.Interval](../../models/components/interval.md)                     | :heavy_check_mark:                                                               | N/A                                                                              |
| `OrderLineItemID`                                                                | `*string`                                                                        | :heavy_minus_sign:                                                               | When set, scope the wipe to this line's intervals only (per-line cell-edit path) |