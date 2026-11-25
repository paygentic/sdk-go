# GetCreditPoolLedgerResponse

Pool ledger for the requested window. The shape depends on whether `granularity` was set: unset returns itemized `entries`, set returns rolled-up `buckets`.


## Supported Types

### CreditPoolLedgerItemizedResponse

```go
getCreditPoolLedgerResponse := operations.CreateGetCreditPoolLedgerResponseCreditPoolLedgerItemizedResponse(components.CreditPoolLedgerItemizedResponse{/* values here */})
```

### CreditPoolLedgerBucketedResponse

```go
getCreditPoolLedgerResponse := operations.CreateGetCreditPoolLedgerResponseCreditPoolLedgerBucketedResponse(components.CreditPoolLedgerBucketedResponse{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch getCreditPoolLedgerResponse.Type {
	case operations.GetCreditPoolLedgerResponseTypeCreditPoolLedgerItemizedResponse:
		// getCreditPoolLedgerResponse.CreditPoolLedgerItemizedResponse is populated
	case operations.GetCreditPoolLedgerResponseTypeCreditPoolLedgerBucketedResponse:
		// getCreditPoolLedgerResponse.CreditPoolLedgerBucketedResponse is populated
	default:
		// Unknown type - use getCreditPoolLedgerResponse.GetUnknownRaw() for raw JSON
}
```
