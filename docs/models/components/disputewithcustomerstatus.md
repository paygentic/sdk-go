# DisputeWithCustomerStatus

Current status of the dispute

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.DisputeWithCustomerStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.DisputeWithCustomerStatus("custom_value")
```


## Values

| Name                                | Value                               |
| ----------------------------------- | ----------------------------------- |
| `DisputeWithCustomerStatusPending`  | pending                             |
| `DisputeWithCustomerStatusAccepted` | accepted                            |
| `DisputeWithCustomerStatusDeclined` | declined                            |