# PriceRateType

What properties.unitPrice is denominated in. 'amount' (the default) is an amount of the invoice currency for each unit metered, so the quantity is the multiplier. 'proportion' is the reverse: a dimensionless share of a currency-denominated quantity, so '0.02' is 2% and the invoice prints '2.00%'. Presentation only. Requires a standard metered price in real currency.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PriceRateTypeAmount

// Open enum: custom values can be created with a direct type cast
custom := components.PriceRateType("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `PriceRateTypeAmount`     | amount                    |
| `PriceRateTypeProportion` | proportion                |