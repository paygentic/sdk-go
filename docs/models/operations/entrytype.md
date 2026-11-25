# EntryType

Restrict the response to a single entry type: `increment` (grant funding, including recurrence refills), `decrement` (usage drawdown), `void` (early grant termination), or `expiration` (unused balance lapsing at a grant's expiry). When `granularity` is also set, this filter scopes which entries feed each bucket's net fields and `entryCount`, but never the reported balances.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.EntryTypeIncrement
```


## Values

| Name                  | Value                 |
| --------------------- | --------------------- |
| `EntryTypeIncrement`  | increment             |
| `EntryTypeDecrement`  | decrement             |
| `EntryTypeVoid`       | void                  |
| `EntryTypeExpiration` | expiration            |