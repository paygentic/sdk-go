# PaymentSessionStatus

Lifecycle status of the session.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PaymentSessionStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.PaymentSessionStatus("custom_value")
```


## Values

| Name                             | Value                            |
| -------------------------------- | -------------------------------- |
| `PaymentSessionStatusPending`    | pending                          |
| `PaymentSessionStatusProcessing` | processing                       |
| `PaymentSessionStatusCompleted`  | completed                        |
| `PaymentSessionStatusFailed`     | failed                           |
| `PaymentSessionStatusExpired`    | expired                          |
| `PaymentSessionStatusCancelled`  | cancelled                        |