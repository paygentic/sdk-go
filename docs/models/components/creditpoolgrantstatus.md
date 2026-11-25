# CreditPoolGrantStatus

Where the grant stands now. `active` grants have started and are neither expired nor voided; a fully used grant stays `active` with a `remainingBalance` of 0. `scheduled` grants start later. `expired` grants passed their expiry. `voided` grants were cancelled.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.CreditPoolGrantStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.CreditPoolGrantStatus("custom_value")
```


## Values

| Name                             | Value                            |
| -------------------------------- | -------------------------------- |
| `CreditPoolGrantStatusActive`    | active                           |
| `CreditPoolGrantStatusScheduled` | scheduled                        |
| `CreditPoolGrantStatusExpired`   | expired                          |
| `CreditPoolGrantStatusVoided`    | voided                           |