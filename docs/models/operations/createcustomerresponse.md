# CreateCustomerResponse


## Supported Types

### CreateCustomerResponseBody1

```go
createCustomerResponse := operations.CreateCreateCustomerResponseCreateCustomerResponseBody1(operations.CreateCustomerResponseBody1{/* values here */})
```

### CreateCustomerResponseBody2

```go
createCustomerResponse := operations.CreateCreateCustomerResponseCreateCustomerResponseBody2(operations.CreateCustomerResponseBody2{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch createCustomerResponse.Type {
	case operations.CreateCustomerResponseTypeCreateCustomerResponseBody1:
		// createCustomerResponse.CreateCustomerResponseBody1 is populated
	case operations.CreateCustomerResponseTypeCreateCustomerResponseBody2:
		// createCustomerResponse.CreateCustomerResponseBody2 is populated
	default:
		// Unknown type - use createCustomerResponse.GetUnknownRaw() for raw JSON
}
```
