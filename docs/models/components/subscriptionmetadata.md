# SubscriptionMetadata


## Supported Types

### 

```go
subscriptionMetadata := components.CreateSubscriptionMetadataStr(string{/* values here */})
```

### 

```go
subscriptionMetadata := components.CreateSubscriptionMetadataNumber(float64{/* values here */})
```

### 

```go
subscriptionMetadata := components.CreateSubscriptionMetadataBoolean(bool{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch subscriptionMetadata.Type {
	case components.SubscriptionMetadataTypeStr:
		// subscriptionMetadata.Str is populated
	case components.SubscriptionMetadataTypeNumber:
		// subscriptionMetadata.Number is populated
	case components.SubscriptionMetadataTypeBoolean:
		// subscriptionMetadata.Boolean is populated
	default:
		// Unknown type - use subscriptionMetadata.GetUnknownRaw() for raw JSON
}
```
