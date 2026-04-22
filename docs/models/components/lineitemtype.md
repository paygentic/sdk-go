# LineItemType

The type of line item. 'discount' line items represent grant discounts with negative subtotal/total amounts.

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

| Name                   | Value                  |
| ---------------------- | ---------------------- |
| `LineItemTypeFee`      | fee                    |
| `LineItemTypeMetered`  | metered                |
| `LineItemTypeManual`   | manual                 |
| `LineItemTypeDiscount` | discount               |