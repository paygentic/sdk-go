# ListEntitlementsResponse

Successfully retrieved the list of entitlements for the customer.


## Fields

| Field                                                                                   | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `Object`                                                                                | [*operations.ListEntitlementsObject](../../models/operations/listentitlementsobject.md) | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `Data`                                                                                  | [][components.EntitlementListItem](../../models/components/entitlementlistitem.md)      | :heavy_check_mark:                                                                      | Array of entitlement list items. The shape of each item varies by featureType.          |
| `Pagination`                                                                            | [components.OffsetPagination](../../models/components/offsetpagination.md)              | :heavy_check_mark:                                                                      | Offset-based pagination response.                                                       |