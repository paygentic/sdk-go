# ListEntitlementGrantsRequest


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `EntitlementID`                                        | `string`                                               | :heavy_check_mark:                                     | The unique identifier of the entitlement.              |
| `Limit`                                                | `*int64`                                               | :heavy_minus_sign:                                     | Maximum number of grants to return per page.           |
| `Offset`                                               | `*int64`                                               | :heavy_minus_sign:                                     | Number of grants to skip.                              |
| `IncludeVoided`                                        | `*bool`                                                | :heavy_minus_sign:                                     | When true, voided grants are included in the response. |