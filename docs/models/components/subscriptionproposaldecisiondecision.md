# SubscriptionProposalDecisionDecision

`approve` creates the subscription and makes the proposal `approved`. `reject` rejects the proposal. Either is final: the proposal never becomes `pending` again.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SubscriptionProposalDecisionDecisionApprove
```


## Values

| Name                                          | Value                                         |
| --------------------------------------------- | --------------------------------------------- |
| `SubscriptionProposalDecisionDecisionApprove` | approve                                       |
| `SubscriptionProposalDecisionDecisionReject`  | reject                                        |