# AdvanceTestClockRequestBody


## Supported Types

### RequestBody1

```go
advanceTestClockRequestBody := operations.CreateAdvanceTestClockRequestBodyRequestBody1(operations.RequestBody1{/* values here */})
```

### RequestBody2

```go
advanceTestClockRequestBody := operations.CreateAdvanceTestClockRequestBodyRequestBody2(operations.RequestBody2{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch advanceTestClockRequestBody.Type {
	case operations.AdvanceTestClockRequestBodyTypeRequestBody1:
		// advanceTestClockRequestBody.RequestBody1 is populated
	case operations.AdvanceTestClockRequestBodyTypeRequestBody2:
		// advanceTestClockRequestBody.RequestBody2 is populated
}
```
