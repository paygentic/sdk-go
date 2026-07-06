# ApprovalDecision

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.ApprovalDecisionPending

// Open enum: custom values can be created with a direct type cast
custom := components.ApprovalDecision("custom_value")
```


## Values

| Name                        | Value                       |
| --------------------------- | --------------------------- |
| `ApprovalDecisionPending`   | pending                     |
| `ApprovalDecisionApproved`  | approved                    |
| `ApprovalDecisionRejected`  | rejected                    |
| `ApprovalDecisionCancelled` | cancelled                   |