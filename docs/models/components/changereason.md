# ChangeReason

Why a change was made. `correction` fixes data to match what was agreed; `migration` moves a contract from another system; `commercial` is a real change to the deal. Defaults to `unspecified`.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.ChangeReasonCommercial

// Open enum: custom values can be created with a direct type cast
custom := components.ChangeReason("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `ChangeReasonCommercial`  | commercial                |
| `ChangeReasonCorrection`  | correction                |
| `ChangeReasonMigration`   | migration                 |
| `ChangeReasonUnspecified` | unspecified               |