# BulkApproveSourceEventsDetails


## Fields

| Field                                                    | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `Processed`                                              | []`string`                                               | :heavy_minus_sign:                                       | IDs of successfully processed events                     |
| `Failed`                                                 | [][operations.Failed](../../models/operations/failed.md) | :heavy_minus_sign:                                       | Failed events with error messages                        |