# SourceEventStatus

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.SourceEventStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.SourceEventStatus("custom_value")
```


## Values

| Name                         | Value                        |
| ---------------------------- | ---------------------------- |
| `SourceEventStatusPending`   | pending                      |
| `SourceEventStatusProcessed` | processed                    |
| `SourceEventStatusFailed`    | failed                       |
| `SourceEventStatusRejected`  | rejected                     |