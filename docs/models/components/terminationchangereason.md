# TerminationChangeReason

Why the subscription was terminated. Null while it is not terminated.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.TerminationChangeReasonCommercial

// Open enum: custom values can be created with a direct type cast
custom := components.TerminationChangeReason("custom_value")
```


## Values

| Name                                 | Value                                |
| ------------------------------------ | ------------------------------------ |
| `TerminationChangeReasonCommercial`  | commercial                           |
| `TerminationChangeReasonCorrection`  | correction                           |
| `TerminationChangeReasonMigration`   | migration                            |
| `TerminationChangeReasonUnspecified` | unspecified                          |