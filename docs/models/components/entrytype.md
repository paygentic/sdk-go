# EntryType

What kind of balance movement this entry represents.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.EntryTypeIncrement

// Open enum: custom values can be created with a direct type cast
custom := components.EntryType("custom_value")
```


## Values

| Name                  | Value                 |
| --------------------- | --------------------- |
| `EntryTypeIncrement`  | increment             |
| `EntryTypeDecrement`  | decrement             |
| `EntryTypeVoid`       | void                  |
| `EntryTypeExpiration` | expiration            |