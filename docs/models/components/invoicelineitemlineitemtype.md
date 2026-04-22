# InvoiceLineItemLineItemType

Type of line item: 'charge' for regular billing, 'refund' for refunded items (amounts are negated)

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.InvoiceLineItemLineItemTypeCharge

// Open enum: custom values can be created with a direct type cast
custom := components.InvoiceLineItemLineItemType("custom_value")
```


## Values

| Name                                | Value                               |
| ----------------------------------- | ----------------------------------- |
| `InvoiceLineItemLineItemTypeCharge` | charge                              |
| `InvoiceLineItemLineItemTypeRefund` | refund                              |