# SubscriptionProposalRejectionReason

Why a person rejected the proposal. `price_mismatch`: a price or discount is not the one agreed. `wrong_plan`: the proposal names the wrong plan. `wrong_start_date`: the start date is wrong. `wrong_customer`: the proposal names the wrong customer. `duplicate`: the customer already has this subscription, or another proposal holds it. `other`: another reason, explained in `text`.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SubscriptionProposalRejectionReasonPriceMismatch

// Open enum: custom values can be created with a direct type cast
custom := components.SubscriptionProposalRejectionReason("custom_value")
```


## Values

| Name                                                | Value                                               |
| --------------------------------------------------- | --------------------------------------------------- |
| `SubscriptionProposalRejectionReasonPriceMismatch`  | price_mismatch                                      |
| `SubscriptionProposalRejectionReasonWrongPlan`      | wrong_plan                                          |
| `SubscriptionProposalRejectionReasonWrongStartDate` | wrong_start_date                                    |
| `SubscriptionProposalRejectionReasonWrongCustomer`  | wrong_customer                                      |
| `SubscriptionProposalRejectionReasonDuplicate`      | duplicate                                           |
| `SubscriptionProposalRejectionReasonOther`          | other                                               |