# EntitlementStatus

Current status of the entitlement.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.EntitlementStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.EntitlementStatus("custom_value")
```


## Values

| Name                        | Value                       |
| --------------------------- | --------------------------- |
| `EntitlementStatusActive`   | active                      |
| `EntitlementStatusCanceled` | canceled                    |
| `EntitlementStatusExpired`  | expired                     |