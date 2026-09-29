# OrderBillingScheduleStatus

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.OrderBillingScheduleStatusDraft

// Open enum: custom values can be created with a direct type cast
custom := components.OrderBillingScheduleStatus("custom_value")
```


## Values

| Name                                  | Value                                 |
| ------------------------------------- | ------------------------------------- |
| `OrderBillingScheduleStatusDraft`     | draft                                 |
| `OrderBillingScheduleStatusActive`    | active                                |
| `OrderBillingScheduleStatusCompleted` | completed                             |
| `OrderBillingScheduleStatusCancelled` | cancelled                             |