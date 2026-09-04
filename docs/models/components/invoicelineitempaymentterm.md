# InvoiceLineItemPaymentTerm

When this line falls due relative to the window it covers: `in_advance` at the window's start, `in_arrears` at its end. A metered line is stamped `in_arrears`, because usage is only known once the window closes — but metered rows written before that rule carry `null` and were never backfilled, so do not read a metered line's term as guaranteed. `null` also means the line is not billed on a term of its own: manual, grant-discount and adjustment lines carry no term, and an adjustment instead falls due with the charge it reduces. Treat `null` as an expected value on any line type, not an error.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.InvoiceLineItemPaymentTermInAdvance

// Open enum: custom values can be created with a direct type cast
custom := components.InvoiceLineItemPaymentTerm("custom_value")
```


## Values

| Name                                  | Value                                 |
| ------------------------------------- | ------------------------------------- |
| `InvoiceLineItemPaymentTermInAdvance` | in_advance                            |
| `InvoiceLineItemPaymentTermInArrears` | in_arrears                            |