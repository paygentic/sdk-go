# BillingCadence

ISO 8601 duration for the billing period.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.BillingCadenceP1M

// Open enum: custom values can be created with a direct type cast
custom := components.BillingCadence("custom_value")
```


## Values

| Name                | Value               |
| ------------------- | ------------------- |
| `BillingCadenceP1M` | P1M                 |
| `BillingCadenceP3M` | P3M                 |
| `BillingCadenceP1Y` | P1Y                 |