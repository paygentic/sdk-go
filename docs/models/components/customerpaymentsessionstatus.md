# CustomerPaymentSessionStatus

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.CustomerPaymentSessionStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.CustomerPaymentSessionStatus("custom_value")
```


## Values

| Name                                     | Value                                    |
| ---------------------------------------- | ---------------------------------------- |
| `CustomerPaymentSessionStatusPending`    | pending                                  |
| `CustomerPaymentSessionStatusProcessing` | processing                               |
| `CustomerPaymentSessionStatusCompleted`  | completed                                |
| `CustomerPaymentSessionStatusFailed`     | failed                                   |
| `CustomerPaymentSessionStatusExpired`    | expired                                  |
| `CustomerPaymentSessionStatusCancelled`  | cancelled                                |