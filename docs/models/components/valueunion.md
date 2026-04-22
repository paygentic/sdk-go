# ValueUnion

The value to compare against


## Supported Types

### 

```go
valueUnion := components.CreateValueUnionStr(string{/* values here */})
```

### 

```go
valueUnion := components.CreateValueUnionNumber(float64{/* values here */})
```

### Value

```go
valueUnion := components.CreateValueUnionValue(components.Value{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch valueUnion.Type {
	case components.ValueUnionTypeStr:
		// valueUnion.Str is populated
	case components.ValueUnionTypeNumber:
		// valueUnion.Number is populated
	case components.ValueUnionTypeValue:
		// valueUnion.Value is populated
	default:
		// Unknown type - use valueUnion.GetUnknownRaw() for raw JSON
}
```
