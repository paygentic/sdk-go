# EntitlementAccessResultStatus

Current status of the entitlement.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.EntitlementAccessResultStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.EntitlementAccessResultStatus("custom_value")
```


## Values

| Name                                    | Value                                   |
| --------------------------------------- | --------------------------------------- |
| `EntitlementAccessResultStatusActive`   | active                                  |
| `EntitlementAccessResultStatusCanceled` | canceled                                |
| `EntitlementAccessResultStatusExpired`  | expired                                 |