# UpdatePricePaymentTerm

Billing timing preference. For billable metrics: 'instant' (charges immediately) or 'in_arrears' (charges at period end). For fees: 'in_advance' (charges upfront) or 'in_arrears' (charges at period end).

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.UpdatePricePaymentTermInstant
```


## Values

| Name                              | Value                             |
| --------------------------------- | --------------------------------- |
| `UpdatePricePaymentTermInstant`   | instant                           |
| `UpdatePricePaymentTermInArrears` | in_arrears                        |
| `UpdatePricePaymentTermInAdvance` | in_advance                        |