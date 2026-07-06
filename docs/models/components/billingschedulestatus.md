# BillingScheduleStatus

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.BillingScheduleStatusDraft

// Open enum: custom values can be created with a direct type cast
custom := components.BillingScheduleStatus("custom_value")
```


## Values

| Name                             | Value                            |
| -------------------------------- | -------------------------------- |
| `BillingScheduleStatusDraft`     | draft                            |
| `BillingScheduleStatusActive`    | active                           |
| `BillingScheduleStatusCompleted` | completed                        |
| `BillingScheduleStatusCancelled` | cancelled                        |