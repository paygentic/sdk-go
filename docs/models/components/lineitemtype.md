# LineItemType

The type of line item. 'discount' and 'adjustment' line items have negative subtotal/total amounts: 'discount' is a grant discount, 'adjustment' is a discount agreed on the subscription.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.LineItemTypeFee

// Open enum: custom values can be created with a direct type cast
custom := components.LineItemType("custom_value")
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `LineItemTypeFee`        | fee                      |
| `LineItemTypeMetered`    | metered                  |
| `LineItemTypeManual`     | manual                   |
| `LineItemTypeDiscount`   | discount                 |
| `LineItemTypeAdjustment` | adjustment               |