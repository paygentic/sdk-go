# UpdateCostAggregation

Updated aggregation method (metered costs only).

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.UpdateCostAggregationSum
```


## Values

| Name                               | Value                              |
| ---------------------------------- | ---------------------------------- |
| `UpdateCostAggregationSum`         | SUM                                |
| `UpdateCostAggregationCount`       | COUNT                              |
| `UpdateCostAggregationAvg`         | AVG                                |
| `UpdateCostAggregationMin`         | MIN                                |
| `UpdateCostAggregationMax`         | MAX                                |
| `UpdateCostAggregationUniqueCount` | UNIQUE_COUNT                       |
| `UpdateCostAggregationLatest`      | LATEST                             |