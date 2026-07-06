# ScheduleInvoiceStatus

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.ScheduleInvoiceStatusStaged

// Open enum: custom values can be created with a direct type cast
custom := components.ScheduleInvoiceStatus("custom_value")
```


## Values

| Name                             | Value                            |
| -------------------------------- | -------------------------------- |
| `ScheduleInvoiceStatusStaged`    | staged                           |
| `ScheduleInvoiceStatusPushed`    | pushed                           |
| `ScheduleInvoiceStatusCancelled` | cancelled                        |