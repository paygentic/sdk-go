# OrderApprovalDecision

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.OrderApprovalDecisionPending

// Open enum: custom values can be created with a direct type cast
custom := components.OrderApprovalDecision("custom_value")
```


## Values

| Name                             | Value                            |
| -------------------------------- | -------------------------------- |
| `OrderApprovalDecisionPending`   | pending                          |
| `OrderApprovalDecisionApproved`  | approved                         |
| `OrderApprovalDecisionRejected`  | rejected                         |
| `OrderApprovalDecisionCancelled` | cancelled                        |