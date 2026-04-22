# SchemasEntitlementStatus

Current status of the entitlement.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SchemasEntitlementStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.SchemasEntitlementStatus("custom_value")
```


## Values

| Name                               | Value                              |
| ---------------------------------- | ---------------------------------- |
| `SchemasEntitlementStatusActive`   | active                             |
| `SchemasEntitlementStatusCanceled` | canceled                           |
| `SchemasEntitlementStatusExpired`  | expired                            |