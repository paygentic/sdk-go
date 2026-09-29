# PlanLineRef

Either a price ID on its own, or a price ID with the key that names its line.


## Supported Types

### PriceID

```go
planLineRef := components.CreatePlanLineRefPriceID(string{/* values here */})
```

### PlanLineInput

```go
planLineRef := components.CreatePlanLineRefPlanLineInput(components.PlanLineInput{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch planLineRef.Type {
	case components.PlanLineRefTypePriceID:
		// planLineRef.PriceID is populated
	case components.PlanLineRefTypePlanLineInput:
		// planLineRef.PlanLineInput is populated
}
```
