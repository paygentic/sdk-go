# GetProfitabilityBucketWidth

Time bucket granularity for the per-customer revenue trend. When omitted, the server picks a reasonable bucket from the window length.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.GetProfitabilityBucketWidthHour
```


## Values

| Name                              | Value                             |
| --------------------------------- | --------------------------------- |
| `GetProfitabilityBucketWidthHour` | hour                              |
| `GetProfitabilityBucketWidthDay`  | day                               |
| `GetProfitabilityBucketWidthWeek` | week                              |