# EntityType

Filter by the kind of entity the session pays for.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.EntityTypeInvoice
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `EntityTypeInvoice`      | invoice                  |
| `EntityTypeSubscription` | subscription             |
| `EntityTypePayment`      | payment                  |
| `EntityTypeTopup`        | topup                    |