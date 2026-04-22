# EventType

Type of event: 'usage' for billable metric events, 'fee' for fee events, 'discount' for grant discount line items (subtotal/total are negative, representing a credit)

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.EventTypeUsage

// Open enum: custom values can be created with a direct type cast
custom := components.EventType("custom_value")
```


## Values

| Name                | Value               |
| ------------------- | ------------------- |
| `EventTypeUsage`    | usage               |
| `EventTypeFee`      | fee                 |
| `EventTypeDiscount` | discount            |