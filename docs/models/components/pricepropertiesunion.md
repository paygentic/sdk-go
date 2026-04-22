# PricePropertiesUnion


## Supported Types

### PriceProperties1

```go
pricePropertiesUnion := components.CreatePricePropertiesUnionPriceProperties1(components.PriceProperties1{/* values here */})
```

### PriceProperties2

```go
pricePropertiesUnion := components.CreatePricePropertiesUnionPriceProperties2(components.PriceProperties2{/* values here */})
```

### PriceProperties3

```go
pricePropertiesUnion := components.CreatePricePropertiesUnionPriceProperties3(components.PriceProperties3{/* values here */})
```

### PriceProperties4

```go
pricePropertiesUnion := components.CreatePricePropertiesUnionPriceProperties4(components.PriceProperties4{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch pricePropertiesUnion.Type {
	case components.PricePropertiesUnionTypePriceProperties1:
		// pricePropertiesUnion.PriceProperties1 is populated
	case components.PricePropertiesUnionTypePriceProperties2:
		// pricePropertiesUnion.PriceProperties2 is populated
	case components.PricePropertiesUnionTypePriceProperties3:
		// pricePropertiesUnion.PriceProperties3 is populated
	case components.PricePropertiesUnionTypePriceProperties4:
		// pricePropertiesUnion.PriceProperties4 is populated
	default:
		// Unknown type - use pricePropertiesUnion.GetUnknownRaw() for raw JSON
}
```
