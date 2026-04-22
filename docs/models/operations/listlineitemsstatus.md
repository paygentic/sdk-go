# ListLineItemsStatus

Filter by line item status. 'pending' returns items not yet on an invoice, 'invoiced' returns items already assigned to an invoice. Omit to return both. Cannot be combined with invoiceId — when filtering by invoice ID all statuses are returned.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.ListLineItemsStatusPending
```


## Values

| Name                          | Value                         |
| ----------------------------- | ----------------------------- |
| `ListLineItemsStatusPending`  | pending                       |
| `ListLineItemsStatusInvoiced` | invoiced                      |