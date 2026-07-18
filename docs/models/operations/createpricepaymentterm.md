# CreatePricePaymentTerm

Billing timing preference: 'in_advance' (prepaid — charged upfront or drawn from a prepaid commitment) or 'in_arrears' (charged at period end).

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.CreatePricePaymentTermInArrears
```


## Values

| Name                              | Value                             |
| --------------------------------- | --------------------------------- |
| `CreatePricePaymentTermInArrears` | in_arrears                        |
| `CreatePricePaymentTermInAdvance` | in_advance                        |