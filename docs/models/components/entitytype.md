# EntityType

The type of Paygentic entity this external reference points at

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.EntityTypeItem

// Open enum: custom values can be created with a direct type cast
custom := components.EntityType("custom_value")
```


## Values

| Name                 | Value                |
| -------------------- | -------------------- |
| `EntityTypeItem`     | item                 |
| `EntityTypeCustomer` | customer             |