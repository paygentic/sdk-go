# LineItemPaymentTerm

Payment term for fee items. Null for metered/manual lines. `null` is listed in the enum as well as via `nullable` because OpenAPI 3.0 validators check the enum independently — `nullable: true` alone does not admit it, and createLineItem (which always returns null here) was emitting a schema-violating body.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.LineItemPaymentTermInAdvance

// Open enum: custom values can be created with a direct type cast
custom := components.LineItemPaymentTerm("custom_value")
```


## Values

| Name                           | Value                          |
| ------------------------------ | ------------------------------ |
| `LineItemPaymentTermInAdvance` | in_advance                     |
| `LineItemPaymentTermInArrears` | in_arrears                     |