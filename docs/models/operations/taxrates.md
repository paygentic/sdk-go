# TaxRates


## Supported Types

### 

```go
taxRates := operations.CreateTaxRatesNumber(float64{/* values here */})
```

### 

```go
taxRates := operations.CreateTaxRatesMapOfTaxRates(map[string]float64{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch taxRates.Type {
	case operations.TaxRatesTypeNumber:
		// taxRates.Number is populated
	case operations.TaxRatesTypeMapOfTaxRates:
		// taxRates.MapOfTaxRates is populated
}
```
