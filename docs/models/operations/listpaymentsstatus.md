# ListPaymentsStatus

Filter by payment status.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.ListPaymentsStatusPending
```


## Values

| Name                           | Value                          |
| ------------------------------ | ------------------------------ |
| `ListPaymentsStatusPending`    | pending                        |
| `ListPaymentsStatusProcessing` | processing                     |
| `ListPaymentsStatusCompleted`  | completed                      |
| `ListPaymentsStatusExpired`    | expired                        |
| `ListPaymentsStatusCancelled`  | cancelled                      |