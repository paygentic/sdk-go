# PaymentUnion

Payment session details when upfront payment is required, or confirmation of a zero-amount paid invoice


## Supported Types

### PaymentPending

```go
paymentUnion := components.CreatePaymentUnionPending(components.PaymentPending{/* values here */})
```

### PaymentPaid

```go
paymentUnion := components.CreatePaymentUnionPaid(components.PaymentPaid{/* values here */})
```

### PaymentAwaitingApproval

```go
paymentUnion := components.CreatePaymentUnionAwaitingApproval(components.PaymentAwaitingApproval{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch paymentUnion.Type {
	case components.PaymentUnionTypePending:
		// paymentUnion.PaymentPending is populated
	case components.PaymentUnionTypePaid:
		// paymentUnion.PaymentPaid is populated
	case components.PaymentUnionTypeAwaitingApproval:
		// paymentUnion.PaymentAwaitingApproval is populated
	default:
		// Unknown type - use paymentUnion.GetUnknownRaw() for raw JSON
}
```
