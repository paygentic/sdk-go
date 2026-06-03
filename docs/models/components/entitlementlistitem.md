# EntitlementListItem

An entitlement as returned by the list endpoint. The shape varies by featureType. Uses `entitlementId` (not `id`) for backwards compatibility with the original list contract.


## Supported Types

### BooleanEntitlementListItem

```go
entitlementListItem := components.CreateEntitlementListItemBoolean(components.BooleanEntitlementListItem{/* values here */})
```

### StaticEntitlementListItem

```go
entitlementListItem := components.CreateEntitlementListItemStatic(components.StaticEntitlementListItem{/* values here */})
```

### MeteredEntitlementListItem

```go
entitlementListItem := components.CreateEntitlementListItemMetered(components.MeteredEntitlementListItem{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch entitlementListItem.Type {
	case components.EntitlementListItemTypeBoolean:
		// entitlementListItem.BooleanEntitlementListItem is populated
	case components.EntitlementListItemTypeStatic:
		// entitlementListItem.StaticEntitlementListItem is populated
	case components.EntitlementListItemTypeMetered:
		// entitlementListItem.MeteredEntitlementListItem is populated
	default:
		// Unknown type - use entitlementListItem.GetUnknownRaw() for raw JSON
}
```
