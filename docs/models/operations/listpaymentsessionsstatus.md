# ListPaymentSessionsStatus

Filter by payment session status.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.ListPaymentSessionsStatusPending
```


## Values

| Name                                  | Value                                 |
| ------------------------------------- | ------------------------------------- |
| `ListPaymentSessionsStatusPending`    | pending                               |
| `ListPaymentSessionsStatusProcessing` | processing                            |
| `ListPaymentSessionsStatusCompleted`  | completed                             |
| `ListPaymentSessionsStatusFailed`     | failed                                |
| `ListPaymentSessionsStatusExpired`    | expired                               |
| `ListPaymentSessionsStatusCancelled`  | cancelled                             |