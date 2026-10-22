# LineCalculationValue

A decimal string, or a price function.


## Supported Types

### 

```go
lineCalculationValue := components.CreateLineCalculationValueStr(string{/* values here */})
```

### LineCalculationPriceFn

```go
lineCalculationValue := components.CreateLineCalculationValueLineCalculationPriceFn(components.LineCalculationPriceFn{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch lineCalculationValue.Type {
	case components.LineCalculationValueTypeStr:
		// lineCalculationValue.Str is populated
	case components.LineCalculationValueTypeLineCalculationPriceFn:
		// lineCalculationValue.LineCalculationPriceFn is populated
	default:
		// Unknown type - use lineCalculationValue.GetUnknownRaw() for raw JSON
}
```
