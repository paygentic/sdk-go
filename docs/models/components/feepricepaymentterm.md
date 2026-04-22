# FeePricePaymentTerm

When the fee is charged relative to the billing period.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.FeePricePaymentTermInAdvance

// Open enum: custom values can be created with a direct type cast
custom := components.FeePricePaymentTerm("custom_value")
```


## Values

| Name                           | Value                          |
| ------------------------------ | ------------------------------ |
| `FeePricePaymentTermInAdvance` | in_advance                     |
| `FeePricePaymentTermInArrears` | in_arrears                     |