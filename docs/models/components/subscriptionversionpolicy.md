# SubscriptionVersionPolicy

How the subscription follows new versions of its plan. `floating` follows the plan's default version: when the default changes, the subscription bills from the new default from its next billing period. `pinned` keeps the plan version that the subscription holds. A subscription created without a value is `floating`. A change to this value does not change a billing period that has already started.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SubscriptionVersionPolicyFloating

// Open enum: custom values can be created with a direct type cast
custom := components.SubscriptionVersionPolicy("custom_value")
```


## Values

| Name                                | Value                               |
| ----------------------------------- | ----------------------------------- |
| `SubscriptionVersionPolicyFloating` | floating                            |
| `SubscriptionVersionPolicyPinned`   | pinned                              |