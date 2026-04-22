# LineItemPaymentTerm

Payment term for fee items. Null for metered/manual lines

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.LineItemPaymentTermInAdvance

// Open enum: custom values can be created with a direct type cast
custom := components.LineItemPaymentTerm("custom_value")
```


## Values

| Name                           | Value                          |
| ------------------------------ | ------------------------------ |
| `LineItemPaymentTermInAdvance` | in_advance                     |
| `LineItemPaymentTermInArrears` | in_arrears                     |