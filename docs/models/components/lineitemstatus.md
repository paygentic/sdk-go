# LineItemStatus

Whether this item is pending or already on an invoice

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.LineItemStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.LineItemStatus("custom_value")
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `LineItemStatusPending`  | pending                  |
| `LineItemStatusInvoiced` | invoiced                 |