# Operator

The comparison operator to use

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.OperatorEquals

// Open enum: custom values can be created with a direct type cast
custom := components.Operator("custom_value")
```


## Values

| Name                  | Value                 |
| --------------------- | --------------------- |
| `OperatorEquals`      | equals                |
| `OperatorContains`    | contains              |
| `OperatorBetween`     | between               |
| `OperatorGreaterThan` | greaterThan           |
| `OperatorLessThan`    | lessThan              |
| `OperatorDomain`      | domain                |