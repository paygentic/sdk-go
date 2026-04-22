# PaymentStatus

Current status of the payment.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PaymentStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.PaymentStatus("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `PaymentStatusPending`    | pending                   |
| `PaymentStatusProcessing` | processing                |
| `PaymentStatusCompleted`  | completed                 |
| `PaymentStatusExpired`    | expired                   |
| `PaymentStatusCancelled`  | cancelled                 |