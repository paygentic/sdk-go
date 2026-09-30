# SubscriptionIntervalKind

plan_line if the plan version has a line with this priceKey. subscription_owned if it does not, so the interval belongs to this subscription only. After an add, check the kind. A mistyped priceKey creates a subscription_owned interval.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SubscriptionIntervalKindPlanLine

// Open enum: custom values can be created with a direct type cast
custom := components.SubscriptionIntervalKind("custom_value")
```


## Values

| Name                                        | Value                                       |
| ------------------------------------------- | ------------------------------------------- |
| `SubscriptionIntervalKindPlanLine`          | plan_line                                   |
| `SubscriptionIntervalKindSubscriptionOwned` | subscription_owned                          |