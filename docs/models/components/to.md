# To


## Supported Types

### 

```go
to := components.CreateToStr(string{/* values here */})
```

### 

```go
to := components.CreateToNumber(float64{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch to.Type {
	case components.ToTypeStr:
		// to.Str is populated
	case components.ToTypeNumber:
		// to.Number is populated
	default:
		// Unknown type - use to.GetUnknownRaw() for raw JSON
}
```
