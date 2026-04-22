# CostAggregation

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.CostAggregationSum

// Open enum: custom values can be created with a direct type cast
custom := components.CostAggregation("custom_value")
```


## Values

| Name                         | Value                        |
| ---------------------------- | ---------------------------- |
| `CostAggregationSum`         | SUM                          |
| `CostAggregationCount`       | COUNT                        |
| `CostAggregationAvg`         | AVG                          |
| `CostAggregationMin`         | MIN                          |
| `CostAggregationMax`         | MAX                          |
| `CostAggregationUniqueCount` | UNIQUE_COUNT                 |
| `CostAggregationLatest`      | LATEST                       |