# PlanVersionSummaryStatus

Lifecycle status of the version.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PlanVersionSummaryStatusDraft

// Open enum: custom values can be created with a direct type cast
custom := components.PlanVersionSummaryStatus("custom_value")
```


## Values

| Name                                | Value                               |
| ----------------------------------- | ----------------------------------- |
| `PlanVersionSummaryStatusDraft`     | draft                               |
| `PlanVersionSummaryStatusPublished` | published                           |
| `PlanVersionSummaryStatusArchived`  | archived                            |