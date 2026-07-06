# ListApprovalsRequest


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `MerchantID`                                                        | `*string`                                                           | :heavy_minus_sign:                                                  | Filter by merchant                                                  |
| `ResourceType`                                                      | [*operations.ResourceType](../../models/operations/resourcetype.md) | :heavy_minus_sign:                                                  | Filter by resource type                                             |
| `ResourceID`                                                        | `*string`                                                           | :heavy_minus_sign:                                                  | Filter by resource id                                               |
| `Kind`                                                              | [*operations.Kind](../../models/operations/kind.md)                 | :heavy_minus_sign:                                                  | Filter by kind                                                      |
| `Decision`                                                          | [*operations.Decision](../../models/operations/decision.md)         | :heavy_minus_sign:                                                  | Filter by decision                                                  |
| `Limit`                                                             | `*int64`                                                            | :heavy_minus_sign:                                                  | N/A                                                                 |
| `Offset`                                                            | `*int64`                                                            | :heavy_minus_sign:                                                  | N/A                                                                 |