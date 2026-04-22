# Code

Optional semantic business error code for machine-readable discrimination (e.g. 'TAX_NOT_ENABLED'). UPPER_SNAKE_CASE. Clients should check this field, not message.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.CodeTaxNotEnabled

// Open enum: custom values can be created with a direct type cast
custom := components.Code("custom_value")
```


## Values

| Name                        | Value                       |
| --------------------------- | --------------------------- |
| `CodeTaxNotEnabled`         | TAX_NOT_ENABLED             |
| `CodePaymentSessionExpired` | PAYMENT_SESSION_EXPIRED     |