# BillableMetricAggregation

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.BillableMetricAggregationSum

// Open enum: custom values can be created with a direct type cast
custom := components.BillableMetricAggregation("custom_value")
```


## Values

| Name                                   | Value                                  |
| -------------------------------------- | -------------------------------------- |
| `BillableMetricAggregationSum`         | SUM                                    |
| `BillableMetricAggregationCount`       | COUNT                                  |
| `BillableMetricAggregationAvg`         | AVG                                    |
| `BillableMetricAggregationMin`         | MIN                                    |
| `BillableMetricAggregationMax`         | MAX                                    |
| `BillableMetricAggregationUniqueCount` | UNIQUE_COUNT                           |
| `BillableMetricAggregationLatest`      | LATEST                                 |