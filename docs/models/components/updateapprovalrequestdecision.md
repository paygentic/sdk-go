# UpdateApprovalRequestDecision

approved/rejected: reviewer decision (maker-checker enforced). cancelled: recall a pending approval or reopen an approved one.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.UpdateApprovalRequestDecisionApproved
```


## Values

| Name                                     | Value                                    |
| ---------------------------------------- | ---------------------------------------- |
| `UpdateApprovalRequestDecisionApproved`  | approved                                 |
| `UpdateApprovalRequestDecisionRejected`  | rejected                                 |
| `UpdateApprovalRequestDecisionCancelled` | cancelled                                |