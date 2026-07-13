# Reason

Coded failure reason. `grant_mint_failed` means the entitlement was created but its initial metered grant could not be minted; re-running this reconciliation retries the mint.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.ReasonEntitlementFailed

// Open enum: custom values can be created with a direct type cast
custom := components.Reason("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `ReasonEntitlementFailed` | entitlement_failed        |
| `ReasonGrantMintFailed`   | grant_mint_failed         |