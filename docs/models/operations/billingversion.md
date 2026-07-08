# BillingVersion

Billing engine version. Only 1 (Standard, line-item billing with metered usage support) is accepted for new plans; omitting the field defaults to 1. 0 (Legacy, fee-schedule billing) is rejected — it exists only on plans created before this restriction.

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