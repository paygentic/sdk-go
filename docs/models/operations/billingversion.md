# BillingVersion

Billing engine version. 0 = legacy fee-schedule billing (Legacy), 1 = line-item billing with metered usage support (Standard).

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/operations"
)

value := operations.BillingVersionZero
```


## Values

| Name                 | Value                |
| -------------------- | -------------------- |
| `BillingVersionZero` | 0                    |
| `BillingVersionOne`  | 1                    |