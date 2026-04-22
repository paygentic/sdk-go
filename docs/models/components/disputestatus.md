# DisputeStatus

Current status of the dispute

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.DisputeStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.DisputeStatus("custom_value")
```


## Values

| Name                    | Value                   |
| ----------------------- | ----------------------- |
| `DisputeStatusPending`  | pending                 |
| `DisputeStatusAccepted` | accepted                |
| `DisputeStatusDeclined` | declined                |