# PriceModel

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PriceModelStandard

// Open enum: custom values can be created with a direct type cast
custom := components.PriceModel("custom_value")
```


## Values

| Name                   | Value                  |
| ---------------------- | ---------------------- |
| `PriceModelStandard`   | standard               |
| `PriceModelDynamic`    | dynamic                |
| `PriceModelVolume`     | volume                 |
| `PriceModelPercentage` | percentage             |