# CreateCreditPoolPurchaseResponse


## Supported Types

### PoolGrantPurchaseResponse

```go
createCreditPoolPurchaseResponse := operations.CreateCreateCreditPoolPurchaseResponsePoolGrantPurchaseResponse(components.PoolGrantPurchaseResponse{/* values here */})
```

### PoolGrantPurchaseAccepted

```go
createCreditPoolPurchaseResponse := operations.CreateCreateCreditPoolPurchaseResponsePoolGrantPurchaseAccepted(components.PoolGrantPurchaseAccepted{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch createCreditPoolPurchaseResponse.Type {
	case operations.CreateCreditPoolPurchaseResponseTypePoolGrantPurchaseResponse:
		// createCreditPoolPurchaseResponse.PoolGrantPurchaseResponse is populated
	case operations.CreateCreditPoolPurchaseResponseTypePoolGrantPurchaseAccepted:
		// createCreditPoolPurchaseResponse.PoolGrantPurchaseAccepted is populated
	default:
		// Unknown type - use createCreditPoolPurchaseResponse.GetUnknownRaw() for raw JSON
}
```
