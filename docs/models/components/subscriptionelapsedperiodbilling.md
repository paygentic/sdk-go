# SubscriptionElapsedPeriodBilling

Whether this subscription's backdated start bills its elapsed periods, as chosen at creation. `null` for a subscription created before the choice existed. `null` is listed in the enum as well as via `nullable` because the response validator checks the enum independently.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SubscriptionElapsedPeriodBillingNone

// Open enum: custom values can be created with a direct type cast
custom := components.SubscriptionElapsedPeriodBilling("custom_value")
```


## Values

| Name                                        | Value                                       |
| ------------------------------------------- | ------------------------------------------- |
| `SubscriptionElapsedPeriodBillingNone`      | none                                        |
| `SubscriptionElapsedPeriodBillingPerPeriod` | per_period                                  |