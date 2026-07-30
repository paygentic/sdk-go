# PlanVersionStatus

Lifecycle status of the version.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PlanVersionStatusDraft

// Open enum: custom values can be created with a direct type cast
custom := components.PlanVersionStatus("custom_value")
```


## Values

| Name                         | Value                        |
| ---------------------------- | ---------------------------- |
| `PlanVersionStatusDraft`     | draft                        |
| `PlanVersionStatusPublished` | published                    |
| `PlanVersionStatusArchived`  | archived                     |