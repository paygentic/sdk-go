# PricePaymentTerm

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PricePaymentTermInstant

// Open enum: custom values can be created with a direct type cast
custom := components.PricePaymentTerm("custom_value")
```


## Values

| Name                        | Value                       |
| --------------------------- | --------------------------- |
| `PricePaymentTermInstant`   | instant                     |
| `PricePaymentTermInArrears` | in_arrears                  |
| `PricePaymentTermInAdvance` | in_advance                  |