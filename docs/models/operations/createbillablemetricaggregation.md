# CreateBillableMetricAggregation

Aggregation calculation method for metric values.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.CreateBillableMetricAggregationSum
```


## Values

| Name                                         | Value                                        |
| -------------------------------------------- | -------------------------------------------- |
| `CreateBillableMetricAggregationSum`         | SUM                                          |
| `CreateBillableMetricAggregationCount`       | COUNT                                        |
| `CreateBillableMetricAggregationAvg`         | AVG                                          |
| `CreateBillableMetricAggregationMin`         | MIN                                          |
| `CreateBillableMetricAggregationMax`         | MAX                                          |
| `CreateBillableMetricAggregationUniqueCount` | UNIQUE_COUNT                                 |
| `CreateBillableMetricAggregationLatest`      | LATEST                                       |