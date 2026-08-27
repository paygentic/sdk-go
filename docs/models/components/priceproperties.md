# PriceProperties


## Supported Types

### StandardPriceProperties

```go
priceProperties := components.CreatePricePropertiesStandardPriceProperties(components.StandardPriceProperties{/* values here */})
```

### DynamicPriceProperties

```go
priceProperties := components.CreatePricePropertiesDynamicPriceProperties(components.DynamicPriceProperties{/* values here */})
```

### VolumePriceProperties

```go
priceProperties := components.CreatePricePropertiesVolumePriceProperties(components.VolumePriceProperties{/* values here */})
```

### PercentagePriceProperties

```go
priceProperties := components.CreatePricePropertiesPercentagePriceProperties(components.PercentagePriceProperties{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch priceProperties.Type {
	case components.PricePropertiesTypeStandardPriceProperties:
		// priceProperties.StandardPriceProperties is populated
	case components.PricePropertiesTypeDynamicPriceProperties:
		// priceProperties.DynamicPriceProperties is populated
	case components.PricePropertiesTypeVolumePriceProperties:
		// priceProperties.VolumePriceProperties is populated
	case components.PricePropertiesTypePercentagePriceProperties:
		// priceProperties.PercentagePriceProperties is populated
	default:
		// Unknown type - use priceProperties.GetUnknownRaw() for raw JSON
}
```
