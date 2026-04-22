# InvoiceStatus

The current status of the invoice

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.InvoiceStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.InvoiceStatus("custom_value")
```


## Values

| Name                         | Value                        |
| ---------------------------- | ---------------------------- |
| `InvoiceStatusActive`        | ACTIVE                       |
| `InvoiceStatusClosing`       | CLOSING                      |
| `InvoiceStatusClosed`        | CLOSED                       |
| `InvoiceStatusCalculating`   | CALCULATING                  |
| `InvoiceStatusDraft`         | DRAFT                        |
| `InvoiceStatusIssued`        | ISSUED                       |
| `InvoiceStatusPaymentFailed` | PAYMENT_FAILED               |
| `InvoiceStatusPaid`          | PAID                         |
| `InvoiceStatusCancelled`     | CANCELLED                    |
| `InvoiceStatusWrittenOff`    | WRITTEN_OFF                  |
| `InvoiceStatusFailed`        | FAILED                       |