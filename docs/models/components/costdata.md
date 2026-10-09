# CostData

Whether metering recorded usage against a cost for every customer the row covers (`recorded`), some of them (`partial`, only on the 'Other' and 'deleted' rows) or none (`none`). Usage that prices at zero is recorded, so `recorded` with a zero `totalCost` is a measured zero. `none` means no cost data, not a zero cost.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.CostDataRecorded

// Open enum: custom values can be created with a direct type cast
custom := components.CostData("custom_value")
```


## Values

| Name               | Value              |
| ------------------ | ------------------ |
| `CostDataRecorded` | recorded           |
| `CostDataPartial`  | partial            |
| `CostDataNone`     | none               |