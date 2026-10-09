# InvoicePaymentProvider

The payment provider that a hosted payment link routes to.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.InvoicePaymentProviderStripe

// Open enum: custom values can be created with a direct type cast
custom := components.InvoicePaymentProvider("custom_value")
```


## Values

| Name                              | Value                             |
| --------------------------------- | --------------------------------- |
| `InvoicePaymentProviderStripe`    | stripe                            |
| `InvoicePaymentProviderAirwallex` | airwallex                         |