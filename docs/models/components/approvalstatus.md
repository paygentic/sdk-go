# ApprovalStatus

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.ApprovalStatusDraft

// Open enum: custom values can be created with a direct type cast
custom := components.ApprovalStatus("custom_value")
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `ApprovalStatusDraft`    | draft                    |
| `ApprovalStatusPending`  | pending                  |
| `ApprovalStatusApproved` | approved                 |
| `ApprovalStatusRejected` | rejected                 |