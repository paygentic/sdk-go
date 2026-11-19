# SubscriptionProposalStatus

`pending` until a person approves or rejects the proposal.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SubscriptionProposalStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.SubscriptionProposalStatus("custom_value")
```


## Values

| Name                                 | Value                                |
| ------------------------------------ | ------------------------------------ |
| `SubscriptionProposalStatusPending`  | pending                              |
| `SubscriptionProposalStatusApproved` | approved                             |
| `SubscriptionProposalStatusRejected` | rejected                             |