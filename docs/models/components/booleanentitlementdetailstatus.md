# BooleanEntitlementDetailStatus

Current status of the entitlement.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.BooleanEntitlementDetailStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.BooleanEntitlementDetailStatus("custom_value")
```


## Values

| Name                                     | Value                                    |
| ---------------------------------------- | ---------------------------------------- |
| `BooleanEntitlementDetailStatusActive`   | active                                   |
| `BooleanEntitlementDetailStatusCanceled` | canceled                                 |
| `BooleanEntitlementDetailStatusExpired`  | expired                                  |