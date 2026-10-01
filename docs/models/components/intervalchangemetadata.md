# IntervalChangeMetadata


## Supported Types

### 

```go
intervalChangeMetadata := components.CreateIntervalChangeMetadataStr(string{/* values here */})
```

### 

```go
intervalChangeMetadata := components.CreateIntervalChangeMetadataNumber(float64{/* values here */})
```

### 

```go
intervalChangeMetadata := components.CreateIntervalChangeMetadataBoolean(bool{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch intervalChangeMetadata.Type {
	case components.IntervalChangeMetadataTypeStr:
		// intervalChangeMetadata.Str is populated
	case components.IntervalChangeMetadataTypeNumber:
		// intervalChangeMetadata.Number is populated
	case components.IntervalChangeMetadataTypeBoolean:
		// intervalChangeMetadata.Boolean is populated
	default:
		// Unknown type - use intervalChangeMetadata.GetUnknownRaw() for raw JSON
}
```
