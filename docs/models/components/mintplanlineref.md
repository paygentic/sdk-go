# MintPlanLineRef

Either a price ID on its own, or a price ID with the key that names its line.


## Supported Types

### PriceID

```go
mintPlanLineRef := components.CreateMintPlanLineRefPriceID(string{/* values here */})
```

### MintPlanLineInput

```go
mintPlanLineRef := components.CreateMintPlanLineRefMintPlanLineInput(components.MintPlanLineInput{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch mintPlanLineRef.Type {
	case components.MintPlanLineRefTypePriceID:
		// mintPlanLineRef.PriceID is populated
	case components.MintPlanLineRefTypeMintPlanLineInput:
		// mintPlanLineRef.MintPlanLineInput is populated
}
```
