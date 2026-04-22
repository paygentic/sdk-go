# EntitlementTemplate

Template for the entitlement. Boolean for simple on/off features, static for features with configuration, metered for usage-based features.


## Supported Types

### EntitlementTemplateBoolean

```go
entitlementTemplate := components.CreateEntitlementTemplateBoolean(components.EntitlementTemplateBoolean{/* values here */})
```

### EntitlementTemplateStatic

```go
entitlementTemplate := components.CreateEntitlementTemplateStatic(components.EntitlementTemplateStatic{/* values here */})
```

### EntitlementTemplateMetered

```go
entitlementTemplate := components.CreateEntitlementTemplateMetered(components.EntitlementTemplateMetered{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch entitlementTemplate.Type {
	case components.EntitlementTemplateTypeBoolean:
		// entitlementTemplate.EntitlementTemplateBoolean is populated
	case components.EntitlementTemplateTypeStatic:
		// entitlementTemplate.EntitlementTemplateStatic is populated
	case components.EntitlementTemplateTypeMetered:
		// entitlementTemplate.EntitlementTemplateMetered is populated
}
```
