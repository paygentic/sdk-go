# InvoiceRefundStatus

Credit note status

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.InvoiceRefundStatusIssued

// Open enum: custom values can be created with a direct type cast
custom := components.InvoiceRefundStatus("custom_value")
```


## Values

| Name                        | Value                       |
| --------------------------- | --------------------------- |
| `InvoiceRefundStatusIssued` | ISSUED                      |
| `InvoiceRefundStatusVoided` | VOIDED                      |