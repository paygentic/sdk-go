# RecordInvoicePaymentResponse

The invoice is settled, or a new payment link exists. The `method` field identifies the shape: `out_of_band` returns the `PAID` invoice; `hosted_link` returns the provider and the new payment link.


## Supported Types

### OutOfBandPaymentResult

```go
recordInvoicePaymentResponse := operations.CreateRecordInvoicePaymentResponseOutOfBand(components.OutOfBandPaymentResult{/* values here */})
```

### HostedLinkPaymentResult

```go
recordInvoicePaymentResponse := operations.CreateRecordInvoicePaymentResponseHostedLink(components.HostedLinkPaymentResult{/* values here */})
```

## Union Discrimination

Use the `Type` field to determine which variant is active, then access the corresponding field:

```go
switch recordInvoicePaymentResponse.Type {
	case operations.RecordInvoicePaymentResponseTypeOutOfBand:
		// recordInvoicePaymentResponse.OutOfBandPaymentResult is populated
	case operations.RecordInvoicePaymentResponseTypeHostedLink:
		// recordInvoicePaymentResponse.HostedLinkPaymentResult is populated
	default:
		// Unknown type - use recordInvoicePaymentResponse.GetUnknownRaw() for raw JSON
}
```
