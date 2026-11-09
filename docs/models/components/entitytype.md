# EntityType

The type of Paygentic entity this external reference points at. `subscriptionProposal` and `subscription` references link a subscription proposal, and the subscription its approval creates, to the CRM record they come from. They are read-only through these endpoints.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.EntityTypeItem

// Open enum: custom values can be created with a direct type cast
custom := components.EntityType("custom_value")
```


## Values

| Name                             | Value                            |
| -------------------------------- | -------------------------------- |
| `EntityTypeItem`                 | item                             |
| `EntityTypeCustomer`             | customer                         |
| `EntityTypeSubscriptionProposal` | subscriptionProposal             |
| `EntityTypeSubscription`         | subscription                     |