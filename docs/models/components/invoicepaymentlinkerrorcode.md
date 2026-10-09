# InvoicePaymentLinkErrorCode

Why Paygentic cannot create a payment link for the invoice.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.InvoicePaymentLinkErrorCodeInvoiceNotLinkableStatus

// Open enum: custom values can be created with a direct type cast
custom := components.InvoicePaymentLinkErrorCode("custom_value")
```


## Values

| Name                                                  | Value                                                 |
| ----------------------------------------------------- | ----------------------------------------------------- |
| `InvoicePaymentLinkErrorCodeInvoiceNotLinkableStatus` | INVOICE_NOT_LINKABLE_STATUS                           |
| `InvoicePaymentLinkErrorCodeInvoiceNoBalance`         | INVOICE_NO_BALANCE                                    |
| `InvoicePaymentLinkErrorCodeMerchantNoPaymentAccount` | MERCHANT_NO_PAYMENT_ACCOUNT                           |