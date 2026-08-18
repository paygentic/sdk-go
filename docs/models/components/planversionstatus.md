# PlanVersionStatus

Lifecycle status of the version.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.PlanVersionStatusPublished

// Open enum: custom values can be created with a direct type cast
custom := components.PlanVersionStatus("custom_value")
```


## Values

| Name                         | Value                        |
| ---------------------------- | ---------------------------- |
| `PlanVersionStatusPublished` | published                    |
| `PlanVersionStatusArchived`  | archived                     |