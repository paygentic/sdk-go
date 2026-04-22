# StaticEntitlementDetailStatus

Current status of the entitlement.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.StaticEntitlementDetailStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.StaticEntitlementDetailStatus("custom_value")
```


## Values

| Name                                    | Value                                   |
| --------------------------------------- | --------------------------------------- |
| `StaticEntitlementDetailStatusActive`   | active                                  |
| `StaticEntitlementDetailStatusCanceled` | canceled                                |
| `StaticEntitlementDetailStatusExpired`  | expired                                 |