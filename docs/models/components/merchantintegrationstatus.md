# MerchantIntegrationStatus

Connection lifecycle state. Live Ampersand health is separate and not stored here.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.MerchantIntegrationStatusActive

// Open enum: custom values can be created with a direct type cast
custom := components.MerchantIntegrationStatus("custom_value")
```


## Values

| Name                                    | Value                                   |
| --------------------------------------- | --------------------------------------- |
| `MerchantIntegrationStatusActive`       | active                                  |
| `MerchantIntegrationStatusDisconnected` | disconnected                            |
| `MerchantIntegrationStatusError`        | error                                   |