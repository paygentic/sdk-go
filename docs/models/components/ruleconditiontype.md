# RuleConditionType

The type of field to evaluate

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.RuleConditionTypeDate

// Open enum: custom values can be created with a direct type cast
custom := components.RuleConditionType("custom_value")
```


## Values

| Name                             | Value                            |
| -------------------------------- | -------------------------------- |
| `RuleConditionTypeDate`          | date                             |
| `RuleConditionTypeCustomerName`  | customerName                     |
| `RuleConditionTypeCustomerEmail` | customerEmail                    |
| `RuleConditionTypeAmount`        | amount                           |