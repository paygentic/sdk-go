# TaxBehavior

Whether tax is added on top of the price (exclusive) or included in the price (inclusive)

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.TaxBehaviorExclusive

// Open enum: custom values can be created with a direct type cast
custom := components.TaxBehavior("custom_value")
```


## Values

| Name                   | Value                  |
| ---------------------- | ---------------------- |
| `TaxBehaviorExclusive` | exclusive              |
| `TaxBehaviorInclusive` | inclusive              |