# CreateCostAggregation

Aggregation method for the metered event.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.CreateCostAggregationSum
```


## Values

| Name                               | Value                              |
| ---------------------------------- | ---------------------------------- |
| `CreateCostAggregationSum`         | SUM                                |
| `CreateCostAggregationCount`       | COUNT                              |
| `CreateCostAggregationAvg`         | AVG                                |
| `CreateCostAggregationMin`         | MIN                                |
| `CreateCostAggregationMax`         | MAX                                |
| `CreateCostAggregationUniqueCount` | UNIQUE_COUNT                       |
| `CreateCostAggregationLatest`      | LATEST                             |