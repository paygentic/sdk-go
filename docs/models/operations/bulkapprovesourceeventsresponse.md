# BulkApproveSourceEventsResponse

Bulk approval results


## Fields

| Field                                                                                                   | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `Processed`                                                                                             | `*int64`                                                                                                | :heavy_minus_sign:                                                                                      | Number of successfully approved events                                                                  |
| `Failed`                                                                                                | `*int64`                                                                                                | :heavy_minus_sign:                                                                                      | Number of events that failed to process                                                                 |
| `Details`                                                                                               | [*operations.BulkApproveSourceEventsDetails](../../models/operations/bulkapprovesourceeventsdetails.md) | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |