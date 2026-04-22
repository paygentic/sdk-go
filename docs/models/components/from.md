# From


## Supported Types

### 

```go
from := components.CreateFromStr(string{/* values here */})
```

### 

```go
from := components.CreateFromNumber(float64{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch from.Type {
	case components.FromTypeStr:
		// from.Str is populated
	case components.FromTypeNumber:
		// from.Number is populated
	default:
		// Unknown type - use from.GetUnknownRaw() for raw JSON
}
```
