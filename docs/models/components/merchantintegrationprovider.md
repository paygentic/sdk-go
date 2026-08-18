# MerchantIntegrationProvider

External provider a merchant can connect at the tenant level. `netsuite` and `accountsiq` are returned on reads wherever a connection exists, but connecting them is accepted only in local and development environments; elsewhere the connect request is refused with 404.

## Example Usage

```go
import (
	"github.com/paygentic/sdk-go/models/components"
)

value := components.MerchantIntegrationProviderSalesforce

// Open enum: custom values can be created with a direct type cast
custom := components.MerchantIntegrationProvider("custom_value")
```


## Values

| Name                                    | Value                                   |
| --------------------------------------- | --------------------------------------- |
| `MerchantIntegrationProviderSalesforce` | salesforce                              |
| `MerchantIntegrationProviderNetsuite`   | netsuite                                |
| `MerchantIntegrationProviderAccountsiq` | accountsiq                              |