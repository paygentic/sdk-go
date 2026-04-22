# EntitlementDetail

A specific entitlement. The response shape varies by featureType.


## Supported Types

### BooleanEntitlementDetail

```go
entitlementDetail := components.CreateEntitlementDetailBoolean(components.BooleanEntitlementDetail{/* values here */})
```

### StaticEntitlementDetail

```go
entitlementDetail := components.CreateEntitlementDetailStatic(components.StaticEntitlementDetail{/* values here */})
```

### MeteredEntitlementDetail

```go
entitlementDetail := components.CreateEntitlementDetailMetered(components.MeteredEntitlementDetail{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch entitlementDetail.Type {
	case components.EntitlementDetailTypeBoolean:
		// entitlementDetail.BooleanEntitlementDetail is populated
	case components.EntitlementDetailTypeStatic:
		// entitlementDetail.StaticEntitlementDetail is populated
	case components.EntitlementDetailTypeMetered:
		// entitlementDetail.MeteredEntitlementDetail is populated
	default:
		// Unknown type - use entitlementDetail.GetUnknownRaw() for raw JSON
}
```
