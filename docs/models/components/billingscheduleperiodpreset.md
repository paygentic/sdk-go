# BillingSchedulePeriodPreset

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.BillingSchedulePeriodPresetSingle

// Open enum: custom values can be created with a direct type cast
custom := components.BillingSchedulePeriodPreset("custom_value")
```


## Values

| Name                                | Value                               |
| ----------------------------------- | ----------------------------------- |
| `BillingSchedulePeriodPresetSingle` | single                              |
| `BillingSchedulePeriodPresetP1M`    | P1M                                 |
| `BillingSchedulePeriodPresetP3M`    | P3M                                 |
| `BillingSchedulePeriodPresetP6M`    | P6M                                 |
| `BillingSchedulePeriodPresetP1Y`    | P1Y                                 |
| `BillingSchedulePeriodPresetCustom` | custom                              |