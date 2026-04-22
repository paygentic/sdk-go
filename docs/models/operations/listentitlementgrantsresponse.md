# ListEntitlementGrantsResponse

Successfully retrieved the list of grants.


## Fields

| Field                                                                                             | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `Object`                                                                                          | [*operations.ListEntitlementGrantsObject](../../models/operations/listentitlementgrantsobject.md) | :heavy_minus_sign:                                                                                | N/A                                                                                               |
| `Data`                                                                                            | [][components.Grant](../../models/components/grant.md)                                            | :heavy_check_mark:                                                                                | N/A                                                                                               |
| `Pagination`                                                                                      | [components.OffsetPagination](../../models/components/offsetpagination.md)                        | :heavy_check_mark:                                                                                | Offset-based pagination response.                                                                 |