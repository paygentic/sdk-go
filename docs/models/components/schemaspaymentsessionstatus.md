# SchemasPaymentSessionStatus

Lifecycle status of the session.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SchemasPaymentSessionStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.SchemasPaymentSessionStatus("custom_value")
```


## Values

| Name                                    | Value                                   |
| --------------------------------------- | --------------------------------------- |
| `SchemasPaymentSessionStatusPending`    | pending                                 |
| `SchemasPaymentSessionStatusProcessing` | processing                              |
| `SchemasPaymentSessionStatusCompleted`  | completed                               |
| `SchemasPaymentSessionStatusFailed`     | failed                                  |
| `SchemasPaymentSessionStatusExpired`    | expired                                 |
| `SchemasPaymentSessionStatusCancelled`  | cancelled                               |