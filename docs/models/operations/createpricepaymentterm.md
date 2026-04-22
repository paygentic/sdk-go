# CreatePricePaymentTerm

Billing timing preference. For billable metrics: 'instant' (charges immediately) or 'in_arrears' (charges at period end). For fees: 'in_advance' (charges upfront) or 'in_arrears' (charges at period end).

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.CreatePricePaymentTermInstant
```


## Values

| Name                              | Value                             |
| --------------------------------- | --------------------------------- |
| `CreatePricePaymentTermInstant`   | instant                           |
| `CreatePricePaymentTermInArrears` | in_arrears                        |
| `CreatePricePaymentTermInAdvance` | in_advance                        |