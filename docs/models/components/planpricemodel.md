# PlanPriceModel

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PlanPriceModelStandard

// Open enum: custom values can be created with a direct type cast
custom := components.PlanPriceModel("custom_value")
```


## Values

| Name                       | Value                      |
| -------------------------- | -------------------------- |
| `PlanPriceModelStandard`   | standard                   |
| `PlanPriceModelDynamic`    | dynamic                    |
| `PlanPriceModelVolume`     | volume                     |
| `PlanPriceModelPercentage` | percentage                 |