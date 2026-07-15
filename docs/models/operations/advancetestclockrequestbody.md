# AdvanceTestClockRequestBody


## Supported Types

### AdvanceTestClockRequestBody1

```go
advanceTestClockRequestBody := operations.CreateAdvanceTestClockRequestBodyAdvanceTestClockRequestBody1(operations.AdvanceTestClockRequestBody1{/* values here */})
```

### AdvanceTestClockRequestBody2

```go
advanceTestClockRequestBody := operations.CreateAdvanceTestClockRequestBodyAdvanceTestClockRequestBody2(operations.AdvanceTestClockRequestBody2{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch advanceTestClockRequestBody.Type {
	case operations.AdvanceTestClockRequestBodyTypeAdvanceTestClockRequestBody1:
		// advanceTestClockRequestBody.AdvanceTestClockRequestBody1 is populated
	case operations.AdvanceTestClockRequestBodyTypeAdvanceTestClockRequestBody2:
		// advanceTestClockRequestBody.AdvanceTestClockRequestBody2 is populated
}
```
