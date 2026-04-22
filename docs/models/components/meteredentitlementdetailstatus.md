# MeteredEntitlementDetailStatus

Current status of the entitlement.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.MeteredEntitlementDetailStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.MeteredEntitlementDetailStatus("custom_value")
```


## Values

| Name                                     | Value                                    |
| ---------------------------------------- | ---------------------------------------- |
| `MeteredEntitlementDetailStatusActive`   | active                                   |
| `MeteredEntitlementDetailStatusCanceled` | canceled                                 |
| `MeteredEntitlementDetailStatusExpired`  | expired                                  |